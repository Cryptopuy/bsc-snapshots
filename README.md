# *bsc-snapshots*


*\> [geth-snapshots](#geth-snapshots)*

**This geth snapshot is generated with `--tries-verify-mode=none` so it contains no MPT data. You should not build a validator upon this snapshot. [Know more >>>](https://github.com/bnb-chain/bsc/pull/926)**

*\> [erigon-snapshots](#erigon-snapshots)*

Updated every ~24~ 36 hours

Old snapshot deleted ~1~ 12 hours after new snapshot generated

## geth-snapshots


> Database uses [geth(v1.1.23)](https://github.com/bnb-chain/bsc/releases/tag/v1.1.23) for sync


### download

<!-- begin_geth -->

!!! from block [27603141](https://bscscan.com/block/27603141)

#### pipeline download and extract
> skip checksum & uncompress if you used pipeline
```bash
wget https://snapshots.48.club/geth.27603141.tar.lz4 -O - | lz4 -cd | tar xf -
```

#### multithreaded download

```bash
aria2c -s4 -x4 -k100M https://snapshots.48.club/geth.27603141.tar.lz4 -o geth.tar.lz4
```


### checksum

!!! db size 366.30 gb, 373.39 gb after decompression
```bash
> openssl sha256 geth.tar.lz4
SHA256(geth.tar.lz4)= 74aff43634191b443e7ecd26fe61ddc66c9c5eb616b1f2caf625555faab44443
```

<!-- end_geth -->

### uncompress


running a script: _`lz4 -cd geth.tar.lz4 | tar xf -`_


### flags


```bash
--txlookuplimit=0 --syncmode=full --tries-verify-mode=none --pruneancient=true --diffblock=5000
```


## erigon-snapshots


> Database uses [erigon(v1.0.2)](https://github.com/node-real/bsc-erigon/releases/tag/v1.0.2) for sync


### download

<!-- begin_erigon -->

!!! from block [27725865](https://bscscan.com/block/27725865)

#### pipeline download and extract
> skip checksum & uncompress if you used pipeline
```bash
wget https://snapshots.48.club/erigon.27725865.tar.lz4 -O - | lz4 -cd | tar xf -
```

#### multithreaded download

```bash
aria2c -s4 -x4 -k100M https://snapshots.48.club/erigon.27725865.tar.lz4 -o erigon.tar.lz4
```


### checksum

!!! db size 1104.02 gb, 1798.12 gb after decompression
```bash
> openssl sha256 erigon.tar.lz4
SHA256(erigon.tar.lz4)= d471c6e6b08aa6b7663d08b34ef766c5754cb61d07368927da3bed86f4761e40
```

<!-- end_erigon -->


### uncompress


running a script: _`lz4 -cd erigon.tar.lz4 | tar xf -`_


### flags


```bash
--chain=bsc --prune=hrtc --db.pagesize=16k
```
