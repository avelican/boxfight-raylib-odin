# boxfight.xyz

http://boxfight.xyz

A very simple multiplayer fighting game with [Odin](https://github.com/odin-lang/Odin) and [raylib](https://github.com/raysan5/raylib)

Special thanks to Caedo: https://github.com/Caedo/raylib_wasm_odin

---

NOTE: This is the original jam code. 

Main repo is here https://github.com/avelican/boxfight

---

## WARNING

This was written for a game jam: [Low Level Game Dev's 7 day multiplayer game challenge](https://www.youtube.com/watch?v=NbhYi_I5T4A).

Do not expect sanity from anything you find here!

The server does not verify client inputs, so players can exercise their "creativity".

(Also, WASM-JS interop is surprisingly tedious and error-prone.)

---

## NOTE

~~The game server will randomly assign you a world ( e.g. /123456 ).~~

~~You can send this to your friends to play together.~~

Edit: Rooms disabled due to lack of time. Sorry!

There was only one users array, which wouldn't work with multiple rooms.

If you add one users array per game, you can re-enable the rooms logic.

---

## Instructions

You will need both Windows and Linux. (Sorry.)

client side

`build.bat`

server side (linux)

`bun index.ts`

( Get Bun here https://github.com/oven-sh/bun )

The server acts both to serve the files, and as a websocket game server.

It just forwards messages. No game logic handled on server except join/quit messages.

---

## License

I dedicate this work to the public domain, except for the parts I didn't write.

raylib is licensed under zlib https://github.com/raysan5/raylib

jsfxr and its dependency riffwave.js are public domain https://github.com/chr15m/jsfxr

The game client is based on Caedo's repo, which currently has no license. (Awaiting response) https://github.com/Caedo/raylib_wasm_odin/

Software Automatic Mouth https://github.com/discordier/sam

Software Automatic Mouth is reverse engineered from proprietary software, so *technically* illegal, but also... the author attempted to contact them and got no response... so... yeah...

( If you start making millions of dollars with SAM, they might take notice ;)

---

## TODO

NOTE: This repo probably won't get any updates, but these TODOs are kept for your inspiration.

(These bugs are probably fixed in the main repo)

TODO: web audio: sounds get queued and play on first interaction

TODO: prevent "player joined" sound spam on load

TODO: despawn bullets that hit other players ? ( ideally move collision to server, but might take longer )

TODO: limit chat buffer size

TODO: make it so bullet commands only accepted if they apply to the player they came from

TODO: detect, prevent and "discourage" hacking

TODO: autoscroll chat

TODO: filter out zalgo text (people spam it to lag the game)

TODO: make player stand out? white?

TODO: map, walls, line of sight

TODO: variety?
TODO: ? weapon pickups ?

TODO: do not randomize other player color on respawn


TODO: Random spawn pos

TODO: prevent player out of bouns

TODO: camera?

TODO: health bar, regen, healing?

TODO: better integrate chat into game ui

TODO: Feedback on hit other player (currently only when you are hit)

TODO: Make it so chat doesn't move player

TODO: add nginx, http/3 ? I wonder how much difference that makes

TODO: ? Add WebTransport ? I don't think Bun supports it yet and supporting both transport types in a single server might be tricky.

TODO: Fix aiming precision

TODO: Port build.bat to Linux. Should be quite trivial.

TODO: Figure out what Drain means in uWebSockets ... seemed fairly important


But a better protocol should greatly speed up loading, which is currently really bad when far from server due to all the back and forth of the handshake and WS upgrade.

DONE: Run server on port 80 (see server index.ts for instructions)

DONE: Fix load times. (Try wasm-strip and wasm-opt, then gzip)

DONE: Set up a systemd service