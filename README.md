# dht-mirror

[![Slack](http://slack.blockstack.org/badge.svg)](http://slack.blockstack.org/)

DHT mirror for better read/write performance

The DHT mirror accepts writes (and returns the call immediately) and then does the actual write to the DHT in the background. Similarly, for read calls (and this is more important for reads) the calls return from the mirror instead of hitting the DHT. Keeping the mirror consistent with the DHT is actually much easier than normal circumstances because all writes are announced on the blockchain in our system. The mirror can simply watch the blockchain for updates and keep the mirror in sync with the DHT (not implemented yet).

current version requires a modified fork of jsonrpc-ns which can be installed by:

> pip install git+https://github.com/muneeb-ali/jsonrpc-ns.git

WARNING: This repo is under active development.

To start the mirror server:

> twistd -noy mirror/server.tac