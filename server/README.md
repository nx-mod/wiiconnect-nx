# server

The services themselves. Nothing is written yet; this says what each will be.

| | |
|---|---|
| `nas/` | the identity check every other service waits on |
| `wc24/` | the message box the channels are fed through |
| `feeds/` | what Forecast and News draw |
| `contests/` | Everybody Votes and Check Mii Out, which need state |
| `matchmaking/` | players, friends, server lists, and NAT negotiation |

## Running one

A server that needs a certificate authority, a database and a week of setup is a
server nobody runs. The aim is one command and a file of settings, with SQLite
underneath and no dependency that has to be compiled.
