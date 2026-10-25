# Security

I wanted to try post-quantum cryptography in a real project, so online games are end to end encrypted and Firebase never sees the game in plain text.

## How it works

**ML-KEM** (as X-Wing, together with X25519) is used to share a random room key with each player.

**ML-DSA** (together with Ed25519) signs every game update, so players know it really came from the host.

**AES-GCM** encrypts all game state and moves before they are sent to Firebase.

The invite link contains the host's key fingerprint, so another player can't pretend to be the host. Updates have a signed sequence number to stop replays, and the room key changes whenever a player leaves.

The crypto libraries are included in the page with pinned versions instead of loading them from a CDN, and the page has a Content Security Policy. You can run a self-test in Settings.

## Limitations

The host runs the game, so a modified host could cheat with the dice. If you join by typing the code instead of using the invite link, the first host you see is trusted. Firebase can still see player names and who is in which room. Keys are stored in the browser, and JavaScript crypto is not constant time, so side channels are possible.

## Libraries

@noble/post-quantum 0.7.1, @noble/curves 2.4.0, @noble/hashes 2.4.0, @noble/ciphers 2.4.0
