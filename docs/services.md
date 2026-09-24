# What a Wii asks the network for

Four conversations, in the order a console has them.

## 1. NAS: may I?

Before anything else, a console authenticates against `nas.nintendowifi.net`
over HTTPS and receives a token. Every online feature is gated behind it, so
until this answers, nothing else is reached.

It is also the smallest piece: a form-encoded POST, a few fields, and a token
the console carries afterwards.

wii-nx's network layer already treats `nas.` and `naswii.` hosts specially,
which is where it is pointed elsewhere.

## 2. WC24: the message box

WiiConnect24 is a mail system that the console polls on a schedule, and it is
how the channels were fed. A title sends and receives messages of its own kind,
so the same plumbing serves the Forecast Channel's downloads and a friend's
letter.

## 3. The channels' own data

Forecast and News are formatted feeds rather than live services: the channel
draws whatever the data says. Whether the weather is real or invented is a
matter of what the server sends.

Everybody Votes and Check Mii Out need something the others do not - state that
outlives a session, and a population to compare against.

## 4. Matchmaking

The large one, and the one people mean by "online". A game asks a server who
else is playing, is given a list, and then connects to those consoles directly -
which is why NAT negotiation exists and is most of the difficulty.

Wiimmfi has done this for a decade and does it well; AltWFC is the open
implementation most private setups run. This is the service where using the
community's is the sensible default and running your own is for a closed group.

### Where we differ from a real console

A Wii has no choice: the addresses are in the game. Our network layer is ours,
so a game's matchmaking calls can be answered without leaving the machine at
all - two consoles on one network can find each other and connect, with no
server anywhere. That is the first thing to build, because it is the smallest
and it works with no internet.
