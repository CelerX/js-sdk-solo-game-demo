# How to integrate your first HTML5 game into CelerX

This is a simple demo for integrating with CelerX JS SDK with a solo HTML5 game Go!Celer!

## Preparation

### Step 1: Install NodeJS LTS

<https://nodejs.org/en/download/>

### Step 2: Clone the example game repo

<https://github.com/CelerX/js-sdk-solo-game-demo>

### Step 3: Install dependencies

Install game dependencies

`npm install`

Install a random number seed library

`npm install seed-random`

### Step 4: Test run the game

`npm start`

## Integrate CelerX SDK in the game

### Step 5: Download CelerX JS SDK

<https://github.com/CelerX/js-sdk>

Copy minified SDK code and create a file `celerx.js` in `lib` folder

*update*: CelerX-JS SDK is now available on NPM, you can install it via

```
npm install celerxjs
```

### Step 6: Add start game logic

A the top of index.js

```js
import celerx from "./celerx"; // import SDK this way if you copied & pasted the SDK code
import celerx from "celerx"; // import SDK this way if you installed it via 'npm install'
import seed from "seed-random";
```

Inside the p5 sketch

```js
celerx.onStart(() => {
    resetGame();
});
celerx.ready();
```

Inside function `resetGame`

```js
const match = celerx.getMatch();
seed(match && match.sharedRandomSeed, { global: true });
```

### Step 7: Add end game logic

Inside function `endGame`

```js
celerx.submitScore(STATE.score);
```

## Put it on CelerX Platform

Step 8: Build and zip the game

```bash
npm run build
```

Important! After building the game, a new folder "dist" will appear in your project directory. Zip this folder and upload it to CelerX Developer Portal.

Step 9: Download CelerX App from App Store/Google Play

Step 10: Upload the game to CelerX Game Developer Portal

1. Create a new account
2. Create a new game
3. Fill out game information. Make sure you select "Solo Game" for game type
4. Click on "App Assets" at the top
5. Drag and drop your game zip file to upload
6. Click on "Go test it on CelerX"
7. Open CelerX and scan the QR Code
