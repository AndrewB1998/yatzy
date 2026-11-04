# Yatzy

Yatzy in the browser. Play solo, against the bot Botti, or online with up to 9 friends using a room code or an invite link. Works on desktop and mobile, in English and Finnish.

**Play:** https://andrewb1998.github.io/yatzy/

## Features

Online games have chat, quick sticker reactions and a dice battle to decide who starts. You can play a single game, best of 3, best of 5 or first to any number of wins. Each player's scorecard has its own colour, and you can swipe between scorecards. Big hands and Yatzys get their own celebrations.

Botti plays the same multiplayer game but runs entirely on your device. It picks its moves by calculating the expected outcome of every option, chats back and reacts to big moments.

## How it works

The whole game is a single `index.html` hosted on GitHub Pages, written in plain HTML, CSS and JavaScript. Online play uses Firebase for anonymous login and the Realtime Database. The host runs the game and checks every move, and the other players send their moves, chat messages and reactions through their own database entry.
