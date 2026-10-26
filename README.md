# Yatzy

Yatzy in the browser. Play solo or online with up to 5 friends using a room code or an invite link. There's a chat for online games, and it works on desktop and mobile, in English and Finnish.

**Play:** https://andrewb1998.github.io/yatzy/

## How it works

The whole game is a single `index.html` hosted on GitHub Pages, written in plain HTML, CSS and JavaScript. Online play uses Firebase for anonymous login and the Realtime Database. The host runs the game and checks every move, and the other players send their moves and chat messages through their own database entry.
