# The GameCube online

Two different things, and only one of them needs a server.

## LAN: no server, ever

The Broadband Adapter games play on a local network with nothing in between.
See [lan.md](lan.md): Double Dash, Kirby Air Ride, 1080 Avalanche.

## Online: one game

Phantasy Star Online is the GameCube's online story - Episodes I & II, and
Episode III - and Japan also had *Homeland*, whose server is long gone with no
revival to speak of. That is the list.

Sega's servers closed in 2007, and the community replaced them:

| | |
|---|---|
| [Sylverant](https://sylverant.net) | open source, AGPL-3.0, supports the GameCube versions, and can be self-hosted |
| Schthack | long-running, closed |

Sylverant's pieces are on GitHub ([libsylverant](https://github.com/Sylverant/libsylverant),
[shipgate](https://github.com/Sylverant/shipgate), and the login and ship
servers beside them), so a private setup is a matter of running them rather than
writing anything.

## What we do differently

A real GameCube reaches a private server by changing its DNS: the addresses are
in the game, so players point the console at a resolver that lies about where
Sega is.

wii-nx resolves those names itself, so there is nothing to lie to. Choosing a
server is a setting:

```toml
[network]
mode = "self"

[network.self]
pso = "your-server.example"
```

No patched disc, no DNS trick, and a real console pointed at the same server
sees the same game.

## What this means for us

Nothing in this repository has to be written for the GameCube. Its LAN games
need the Broadband Adapter in libgc-nx; its one online game needs a server that
already exists and is open. What is left to us is the client side: the adapter,
the resolver, and saying plainly which server answered.
