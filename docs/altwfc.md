# Running AltWFC for tests

Matchmaking is the one service where writing our own first would be foolish:
[barronwaffles/dwc_network_server_emulator](https://github.com/barronwaffles/dwc_network_server_emulator)
- AltWFC - is the open implementation of what Nintendo's GameSpy servers did,
it has been maintained for a decade, and it already answers what a Wii game
asks. AGPL-3.0, which sits fine beside this repository's GPL-3.0-or-later.

So for testing: run AltWFC, point wii-nx at it, and spend our own effort on the
parts nobody else can do for us - the local path, and the client side.

## What it answers

| | |
|---|---|
| NAS | the identity check, which everything waits on |
| GPCM / GPSP | players, friends, presence |
| server browser | who is hosting, and what |
| NATNEG | introducing two consoles so they can talk directly |
| `gamestats`, `sake` | leaderboards and per-game storage |

## Pointing wii-nx at it

A console has these addresses in its titles and needs them patched. wii-nx does
not: its network layer resolves them, so this is a setting.

```toml
[network]
mode = "self"

[network.self]
# Wherever AltWFC is listening. The DNS names a game asks for are answered
# from here rather than from Nintendo's, and nothing is patched.
nas = "http://192.168.1.10"
gamespy = "192.168.1.10"
```

## What we still write ourselves

AltWFC replaces Nintendo's servers. It cannot do the thing that is only possible
from inside the console:

- **local play with no server at all.** Two machines on one network, discovered
  by broadcast and connected directly, because the matchmaking calls a game
  makes are answered by our own code rather than sent anywhere.
- **saying what happened.** When a game reaches for a service that is not there,
  our network layer knows, and can say so instead of letting the game wait.

## What is ours to keep honest

AltWFC accepts whatever identity a console presents. Ours issues its own -
wii-nx synthesises a serial and a MAC rather than copying a real console's - so
nothing here needs, or wants, anyone's real credentials.
