# PQC Yatzy

I wanted to try post-quantum cryptography in a real project, so I built a multiplayer Yatzy game where online games are end-to-end encrypted and the server never sees the game in plain text.

You can play solo or online with up to 5 friends using a room code or an invite link. Works on desktop and mobile, and in English and Finnish.

**Play:** https://andrewb1998.github.io/yatzy/

## How it works

The game is a single `index.html` hosted on GitHub Pages, written in plain HTML, CSS and JavaScript. Online play uses Firebase (anonymous login and Realtime Database). The host runs the game and checks every move, and the other players send their moves to the host. The database rules let each player write only to their own entry.

## Security

**ML-KEM** (as X-Wing, together with X25519) shares a random room key with each player.

**ML-DSA** (together with Ed25519) signs every game update, so players know it came from the host.

**AES-GCM** encrypts all game events before they go to Firebase, so the server only sees ciphertext.

The invite link contains the host's key fingerprint, so nobody else can pretend to be the host. Updates have a signed sequence number to stop replays, and the room key changes when a player leaves. The crypto libraries are bundled into the page instead of loaded from a CDN, the page has a Content Security Policy, and you can run a self-test in Settings.

## Limitations

The host runs the game, so a modified host could cheat with the dice. If you join by typing the code instead of using the invite link, the first host you see is trusted. Firebase can still see player names and who is in which room. Keys are stored in the browser, and JavaScript crypto is not constant time, so side channels are possible.

Crypto libraries: [noble](https://paulmillr.com/noble/) by Paul Miller (MIT), @noble/post-quantum 0.7.1.
