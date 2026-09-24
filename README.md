# wiiconnect-nx

The services a Wii expects, when Nintendo's are gone.

A Wii asks the network for four things: who it is, whether it may play online,
who else is playing, and what the channels should show. All of that ended in
2013 and 2014. This is a server that answers, and a way to point a console at
one - ours, someone else's, or your own.

Nothing here is Nintendo's. No title is patched and no binary is redistributed:
where a console would look up `nas.nintendowifi.net`, wii-nx's own network layer
is told to look somewhere else, which is a line of configuration rather than a
modified game.

## Three ways to be online

| | What it is | When |
|---|---|---|
| **local** | no server at all: consoles on one network find each other and connect directly | a room with two Switches, or no internet |
| **your own** | [AltWFC](docs/altwfc.md) for games, this server for the channels | a group of friends, a LAN party, or preservation |
| **community** | the services that already exist - [Wiimmfi](https://wiimmfi.de), RWFC, [RiiConnect24](https://riiconnect24.net), [WiiLink](https://wiilink.ca) | everything else |

The third already works: Mario Kart Wii's project here points at RWFC today. The
first is the one a real console cannot do and we can, because the network layer
a game talks to is ours rather than Nintendo's.

## What a console asks for

| Service | Asked by | Here |
|---|---|---|
| **NAS** — is this console allowed | everything, before anything else | first |
| **WC24 mail** — the message box, and what pushes data to channels | the channels, and games with letters | second |
| **Forecast, News** | those two channels | data, once the plumbing is there |
| **Contests** — Everybody Votes, Check Mii Out | those channels | needs state that lasts |
| **Matchmaking** — GameSpy's job: players, friends, server lists, NAT | every game with online play | the large one |

## Identity

A console identifies itself with a serial, a MAC and a certificate signed by
Nintendo. This server issues its own instead, and wii-nx synthesises its own
console identity rather than copying a real one. Nobody's console is cloned,
and no real console's identity is needed to use this.

## Layout

```
server/   the services, and how to run them
client/   the configuration a wii-nx build uses to find a server
docs/     what each service is, and what a console expects of it
```

## License

GPL-3.0-or-later.
