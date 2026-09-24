# TODO - wiiconnect-nx

In the order that gets a console online soonest.

## Local first, because it needs no server

- [ ] Answer a game's matchmaking calls inside wii-nx's own network layer
- [ ] Find other consoles on the network by broadcast, and connect to them
- [ ] Mario Kart Wii as the first case: two Switches, one room, no internet

This is the part a real Wii cannot do. The addresses are in its titles; ours are
in our own code.

## NAS, because everything waits on it

- [ ] The authentication a console does before anything else, and the token it
      carries afterwards
- [ ] Issue our own identities rather than accepting a real console's
- [ ] Point wii-nx at it with a setting, not a patch

## WC24

- [ ] The message box: sending, receiving, and the schedule a console polls on
- [ ] Feed the Forecast and News channels through it

## Matchmaking, properly

- [ ] Players, friends and server lists - GameSpy's job, which AltWFC already
      implements openly
- [ ] NAT negotiation, which is most of the difficulty
- [ ] Decide what is worth running ourselves when Wiimmfi already does this well

## Everything else

- [ ] Contests: Everybody Votes and Check Mii Out, which need state that lasts
- [ ] A settings file and one command to run it, with SQLite underneath
- [ ] Say plainly, in wii-nx, when a game reached for a service that is not there
