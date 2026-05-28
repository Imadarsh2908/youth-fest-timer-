# Youth Fest Server

A small Express.js server for the Youth Fest project. It serves static files, provides event data, and controls Arduino-based traffic light signals.

## Features

- Serves static website assets from `static/`
- Exposes `/yft-data` to return event JSON data from `YFTData.json`
- Handles Arduino control actions via `/arduino/:action`
- Saves event records using `recordhandler.js`
- Includes a restart endpoint to refresh the server when using `nodemon`

## Project Structure

- `index.js` — main Express server entry point
- `arduino.js` — Arduino control module
- `recordhandler.js` — saves event records
- `YFTData.json` — event data storage
- `static/` — public website files (`html`, `css`, `js`, `images`, `audio`)
- `package.json` — Node.js dependencies and scripts

## Installation

```bash
cd "youth-fest-main"
npm install
```

## Run

```bash
npm start
```

This runs `node-dev index.js` as defined in `package.json`.

## Available Routes

- `GET /yft-data`
  - Returns the contents of `YFTData.json`
- `POST /arduino/red`
  - Sends the red light signal
- `POST /arduino/green`
  - Sends the green light signal
- `POST /arduino/yellow`
  - Sends the yellow light signal
- `POST /arduino/off`
  - Turns off the Arduino signal and saves a record from the request body
- `POST /arduino/connect`
  - Connects to the Arduino device
- `POST /refresh-server`
  - Restarts the server when used with `nodemon`

## Notes

- The app uses `body-parser` for JSON and URL-encoded request bodies.
- If you add or rename a dedicated `home/` folder, update the route in `index.js` accordingly.
- If `git push` fails due to non-fast-forward errors, run:

```bash
git pull origin main
``` 

and then push again.

## Dependencies

- `express`
- `body-parser`
- `serialport`
- `csv-writer`
- `node-dev`
