# Playing on one network

The two consoles answer this differently, and it decides how much server is
needed.

## GameCube: real LAN, and no server at all

A GameCube with a Broadband Adapter plays over a local network without asking
anyone's permission. A handful of titles support it, and the best known is
**Mario Kart: Double Dash!!** - eight players across two consoles, with no
matchmaking service involved at any point. Kirby Air Ride and 1080 Avalanche are
in the same group.

For us that means the whole of `wiiconnect-nx` is unnecessary for those games.
What is needed is in libgc-nx and libdol-nx instead:

- the Broadband Adapter, as a device the game's SDK can talk to
- broadcasts that reach the other machine

Two Switches on one network, and the game does the rest. Machines that are not
in the same room can be bridged by a tunnel - which is what
[switch-lan-play-nx](https://github.com/nx-mod/switch-lan-play-nx) already does
for Switch games, and the same trick works here because the traffic is ordinary
UDP broadcast.

## Wii: no LAN, so something has to answer

The Wii skipped local networking and went straight to WiiConnect24 and Nintendo
WFC. A Wii game with multiplayer either shares one screen or goes out to the
internet, and when the internet end is gone the game waits.

Three ways to give it an answer, cheapest first:

1. **Answer it ourselves.** The matchmaking calls a game makes are handled by
   wii-nx's own network layer, which can introduce two consoles on the same
   network directly. No server, no accounts, no internet. This is the thing a
   real Wii cannot do, because on a real Wii that code is Nintendo's.
2. **Run [AltWFC](altwfc.md).** The open implementation of the GameSpy services,
   for a group that wants internet play of its own.
3. **Use the community's.** Wiimmfi and RWFC, which work today.

## What this means for the order of work

The GameCube path is the one with no server in it, and it lands as soon as
libgc-nx exists - the disc is already dumped. The Wii path needs either our own
answering or someone's server, and the first of those is the smaller piece.
