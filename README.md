# Dobby

Dobby is a collaborative code editor. Open a room in two desktop browser windows to edit code together, switch languages, chat, or draw on a shared whiteboard. The video room uses WebRTC for audio and video.

## Run locally

Install Node.js and npm, then clone this repository.

```sh
git clone https://github.com/harshhoneybee/Dobby.git
cd Dobby
```

Open two terminals in the `Dobby` directory. In the first, start the Socket.IO server.

```sh
npm ci --prefix server
npm start --prefix server
```

In the second, start the React client.

```sh
npm ci --prefix client
npm start --prefix client
```

Open [localhost:3000](http://localhost:3000) on a desktop browser. Create a room, then join the same room ID in a second window with another username. Code edits should appear in both windows. The server listens on port 5000.

## Configure your own deployment

| Setting | Where to set it | Purpose |
| --- | --- | --- |
| `REACT_APP_WEB_SOCKET_URL` | Client environment, before starting or building | URL of your Socket.IO server. Development defaults to `http://localhost:5000`. Production defaults to the page’s origin. |
| `CLIENT_ORIGIN` | Server environment, before starting | Exact frontend origin allowed for cross-origin Socket.IO requests. Defaults to `http://localhost:3000`. |
| `PORT` | Server environment | HTTP and Socket.IO port. Defaults to `5000`. |

The React client is in [client/](client/) and the Express and Socket.IO server is in [server/](server/). To host them separately, build the client with `npm run build --prefix client`, publish `client/build`, and point the two settings above at your deployed URLs.

## Project history

This repository is based on [Prayas248/Dobby_New](https://github.com/Prayas248/Dobby_New). The [import commit](https://github.com/harshhoneybee/Dobby/commit/b50b11ee9be411366f85686cccd1146b9b2cd307) records the original version.
