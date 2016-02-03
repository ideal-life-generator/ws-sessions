# ws-sessions

Used with [ws-session](https://www.npmjs.com/package/ws-session) on the client.

Donate: 5300 7211 1281 6316

## *Full session for browser connection.*

In progress.

## Roadmap:

  - Testing possible memory leak under heavy loads;
  - Testing speeds at different implementation strategies;
  - Documentation.

Coming soon...

## Usage

```js
import { Server } from "ws"
import sessions from "ws-sessions"

const wsServer = new Server({ port: 5000 })
const { connections, single, session, all, exceptSingle, exceptSession, subscribe } = sessions(wsServer)
connections(({ socketId, socketSessionId, socket }) => {
  subscribe("greeting.request", (data) => {
    // ...
  })
  single(socketId, "data from server for single socket")
  session(socketSessionId, "data from server for session connections")
  all("data from server for all connections")
  exceptSingle(socketId, "data from server for all connections except single socket")
  exceptSession(socketId, "data from server for all connections except session connections")
})
```