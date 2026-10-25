# Yatzy

Yatzy in the browser. You can play solo or online with up to 5 friends using a room code or an invite link. Works on desktop and mobile, and in English and Finnish.

**Play:** https://andrewb1998.github.io/yatzy/

## How it works

The game is a single `index.html` hosted on GitHub Pages. Online play uses Firebase (anonymous login and Realtime Database). The host runs the game and checks every move, and the other players send their moves to the host.

Multiplayer is end to end encrypted with post-quantum cryptography. It uses ML-KEM to share a room key with each player, ML-DSA to sign every game update so players know it came from the host, and AES-GCM to encrypt all game events before they go to Firebase, so the server only sees ciphertext.

More details in [SECURITY.md](SECURITY.md).

## Built with

Plain HTML, CSS and JavaScript in one file, with no framework or build step. The page contains the game logic, the UI, the Firebase connection and a bundled crypto library. Firebase only relays encrypted messages between players, and the database rules let each player write only to their own entry.

Crypto libraries: [noble](https://paulmillr.com/noble/) by Paul Miller (MIT).
