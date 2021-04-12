# [Go] EtherKV: A Semantics-Awared Key-Value Store for Ethereum System

Before running the EtherKV, we must download historial blocks of Ethereum, run

```bash
geth --syncmode "full" --cache 1024 --datadir "xxx"
```

## Separation storage

We store state data and non-state data in the underlying KV storage respectively, which is implemented by two different interfaces()

```bash
db,_ := ethdb.NewLDBDatabase("PATH")
db.Put(key(non-state), value(nono-state))
db.Put_s(key(state), value(state))
```
## Prefix MPT

Prefix MPT can aggregate nodes that are strongly spatiotemporal, see /MPT/trie for more details

## SGC

```bash
type sgc struct{
  mu sync.Mutex
  capacity int
  trriger int
  rused, fused, r1used, f1used int
  recent lruNode
  frequent lruNode
  r1, f1 lruNode
}
```
See /goleveldb/leveldb/cache for more details 

## How to use

```bash
1. WRITE: Using interface() InsertChain() to replay all historail blocks
2. READ: All tests are located in /MPT/trie/exper_test.go
```
Before running read tests, you must botain all historial transactions hash and all accounts registered
