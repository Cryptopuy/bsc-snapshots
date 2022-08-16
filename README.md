# *bsc-snapshots*


*\> [geth-snapshots](#geth-snapshots)*

*\> [erigon-snapshots](#erigon-snapshots)*

Updated every ~24~ 36 hours

Old snapshot deleted ~1~ 12 hours after new snapshot generated

## geth-snapshots


> Database uses [geth(v1.1.12)](https://github.com/bnb-chain/bsc/releases/tag/v1.1.12) for sync


### download

<!-- begin_geth -->

!!! from block [20477802](https://bscscan.com/block/20477802)
```bash
aria2c -s14 -x14 -k100M https://snapshots.bnb48.club/geth.20477802.tar.lz4 -o geth.tar.lz4
```


### checksum


!!! db size 563.82 gb, 576.09 gb after decompression
```bash
> openssl sha256 geth.tar.lz4
SHA256(geth.tar.lz4)= 65aa833c88a36dfefc5d686de1f7b8a0daba3313106738547829bafae02610f4
```

<!-- end_geth -->

### uncompress


running a script: _`lz4 -cd geth.tar.lz4 | tar xf -`_


### flags


```bash
--txlookuplimit=0 --diffsync=true --syncmode=full --tries-verify-mode=none --pruneancient=true --diffblock=5000
```


## erigon-snapshots


> Database uses [erigon(v2022.07.04)](https://github.com/ledgerwatch/erigon/releases/tag/v2022.07.04) for sync


### download

<!-- begin_erigon -->

!!! from block [20473929](https://bscscan.com/block/20473929)
```bash
aria2c -s14 -x14 -k100M https://snapshots.bnb48.club/erigon.20473929.tar.lz4 -o erigon.tar.lz4
```


### checksum


!!! db size 755.14 gb, 1081.61 gb after decompression
```bash
> openssl sha256 erigon.tar.lz4
SHA256(erigon.tar.lz4)= 1baec1f8242c5f886125d2490c4ff9b600fe86ef604b821de7611d4b0d1d82ce
```

<!-- end_erigon -->

### uncompress


running a script: _`lz4 -cd erigon.tar.lz4 | tar xf -`_


### flags


```bash
--chain=bsc --prune= --prune.h.older=5000 --prune.r.older=5000 --prune.t.older=5000 --prune.c.older=5000 --db.pagesize=16k
```
