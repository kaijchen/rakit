# Rakit

[![Build](https://github.com/kaijchen/rakit/actions/workflows/build.yml/badge.svg?branch=main&event=push)](https://github.com/kaijchen/rakit/actions/workflows/build.yml)
[![codecov](https://codecov.io/github/kaijchen/rakit/branch/main/graph/badge.svg?token=8SIFPXSGFJ)](https://codecov.io/github/kaijchen/rakit)
[![License](https://img.shields.io/github/license/apache/incubator-uniffle)](https://www.apache.org/licenses/LICENSE-2.0)

Rakit is a Raft consensus library implemented in Java.

Raft is a consensus algorithm for managing a replicated log.
For more details on Raft,
see ["In Search of an Understandable Consensus Algorithm"][1]
by Diego Ongaro and John Ousterhout.

[1]: https://raft.github.io/raft.pdf "In Search of an Understandable Consensus Algorithm"

## Features

***Still working in progress.***

* Basics
    * [ ] Leader election
    * [ ] Log replication
    * [ ] Log compaction
    * [ ] Membership changes
* Extensions 
    * [ ] Leadership transfer extension
    * [ ] Efficient linearizable read-only queries served by both the leader and followers
        * leader checks with quorum and bypasses Raft log before processing read-only queries
        * follower asks leader to get a safe read index before processing read-only queries
    * [ ] More efficient lease-based linearizable read-only queries served by both the leader and followers
        * leader bypasses Raft log and processing read-only queries locally
        * follower asks leader to get a safe read index before processing read-only queries
        * this approach relies on the clock of the all the machines in raft group
* Enhancements
    * [ ] Optimistic pipelining to reduce log replication latency
    * [ ] Flow control for log replication
    * [ ] Batching Raft messages to reduce synchronized network I/O calls
    * [ ] Batching log entries to reduce disk synchronized I/O
    * [ ] Writing to leader's disk in parallel
    * [ ] Internal proposal redirection from followers to leader
    * [ ] Automatic stepping down when the leader loses quorum
* Examples
    * [ ] Key-value storage service

## Requirements

* Java 17+

## Build

```shell
$ mvn clean package -DskipTests
```

## Acknowledgments

This project is inspired by [etcd/raft][2] and [Apache Ratis][3].

[2]: https://github.com/etcd-io/raft "Raft library of etcd"
[3]: https://github.com/apache/ratis "Apache Ratis"

## License

Apache-2.0
