# client

What a wii-nx build reads to find a server.

A console has these addresses baked into its titles. wii-nx does not: the
network layer resolves them, so choosing a service is configuration.

```toml
[network]
# "community" uses the services that already exist, "local" needs no server at
# all, and "self" is the one you run.
mode = "community"

[network.self]
nas = "https://wiiconnect.example/nas"
wc24 = "https://wiiconnect.example/wc24"
```

Nothing here patches a title, and a real Wii pointed at the same server sees the
same services.
