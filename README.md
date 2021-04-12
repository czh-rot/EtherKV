# [Go] EtherKV: A Semantics-Awared Key-Value Store for Ethereum System

Before running the EtherKV, we must download historial blocks of Ethereum, run

```bash
geth --syncmode "full" --cache 1024 --datadir "xxx"
```

## Separation storage

We store state data and non-state data in the underlying KV storage respectively, which is implemented by two different interfaces

```bash
db,_ := ethdb.NewLDBDatabase("PATH")
db.Put(key(non-state), value(nono-state))
db.Put_s(key(state), value(state))
```
## Prefix MPT

## SGC

## How to use

```bash
1. WRITE: Using interface() InsertChain() to replay all historail blocks
2. READ: All tests are located in /MPT/trie/exper_test.go
```
