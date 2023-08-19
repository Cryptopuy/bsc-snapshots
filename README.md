# *bsc-snapshots*


- *[Geth](#geth)*
    - *[Geth fast node](#geth-fast-node)*
    - *[Geth full node](#geth-full-node)*
- *[Erigon](#erigon)*
    - *[Erigon fast node](#erigon-fast-node)*
    - *[Erigon archive node](#erigon-archive-node)*
        - *[BSC mainnet](#bsc-mainnet)*
        - *[BSC testnet](#bsc-testnet)*
- *[How to download](#how-to-download)*
    - *[pipeline download and extract](#pipeline-download-and-extract)*
    - *[multithreaded download](#multithreaded-download)*
    - *[download in parts](#download-in-parts)*

## Geth
### Geth fast node

| Field |Value |
| --- | --- |
| Version | [v1.2.10](https://github.com/bnb-chain/bsc/releases/tag/v1.2.10) |
| Block | [30957907](https://bscscan.com/block/30957907) (Aug-18-2023 10:18:35 AM +UTC) |
| Link | `https://snapshots.48.club/geth.fast.30957907.tar.zst` |
| Size | 383.09G <-> 420.46G |
| SHA256 | `8f2e014ba7ba42f42921cdbd33506933fa967b9fdf4d46363068d0ab000ab2f9` |
| Flags | `--txlookuplimit=0 --syncmode=full --tries-verify-mode=none --pruneancient=true` |

[Back to TOC](#bsc-snapshots)

### Geth full node

| Field |Value |
| --- | --- |
| Version | [v1.2.10](https://github.com/bnb-chain/bsc/releases/tag/v1.2.10) |
| Block | [30982623](https://bscscan.com/block/30982623) (Aug-19-2023 06:57:06 AM +UTC) |
| Link | `https://snapshots.48.club/geth.full.30982623.tar.zst` |
| Size | 824.47G <-> 885.40G |
| SHA256 | `8c9e7c7fe20b0c187be77f4bf8347e8768d3de69cbf4574f65669948d6c6154b` |
| Flags | `--txlookuplimit=0 --syncmode=full --tries-verify-mode=local` |

[Back to TOC](#bsc-snapshots)

## Erigon

### Erigon torrents files
| Field |Value |
| --- | --- |
| Usage | [#82](https://github.com/48Club/bsc-snapshots/issues/82) |
| Link | `https://snapshots.48.club/erigon.torrents.20230731.tar.zst` |
| Size | 507.91G <-> 761.19G |
| SHA256 | `af97cefa228a0f7f427937f76477e1fa8c9476186465408cfd4a542e26918e0b`|

### Erigon fast node

| Field |Value |
| --- | --- |
| Version | [v1.1.7](https://github.com/node-real/bsc-erigon/releases/tag/v1.1.7) |
| Block | [30440951](https://bscscan.com/block/30440951) (Jul-31-2023 10:08:07 AM +UTC) |
| Link | `https://snapshots.48.club/erigon.fast.30440951.tar.zst` |
| Size | 472.86G <-> 1218.00G |
| SHA256 | `0f6c6510e3f8dcfbf6353555d55991dd18399a91d02d531c919e296ec8b9b479`|
| Flags | `--chain=bsc --prune=hrtc --db.pagesize=16k` |

[Back to TOC](#bsc-snapshots)

### Erigon archive node

#### BSC mainnet

| Field |Value |
| --- | --- |
| Version | [v1.1.7](https://github.com/node-real/bsc-erigon/releases/tag/v1.1.7) |
| Block | [30452140](https://bscscan.com/block/30452140) (Jul-31-2023 07:29:14 PM +UTC) |
| List | [erigon_archive.list](list/erigon_archive.list?raw=1) |
| Size | 1600.01G <-> 6794.00G |
| SHA256 | `8df2389ef95d990aa1e00885cb5cce778e648f17d88d13379fef2f83cc40c495` |
| Flags | `--chain=bsc --db.pagesize=16k` |

[Back to TOC](#bsc-snapshots)

#### BSC testnet

| Field |Value |
| --- | --- |
| Version | [v1.1.4](https://github.com/node-real/bsc-erigon/releases/tag/v1.1.4) |
| Block | [31436344](https://testnet.bscscan.com/block/31436344) (Jul-10-2023 04:04:58 PM +UTC) |
| Link | `https://snapshots.48.club/erigon.testnet.31436344.tar.zst` |
| Size | 160.59G <-> 594.00G |
| SHA256 | `e8a8484177753c16bfc5711fb06d69dc9bc0c51ed41280cee074ae4554a71e60` |
| Flags | `--chain=chapel --db.pagesize=16k` |

[Back to TOC](#bsc-snapshots)

## How to download
### pipeline download and extract

```bash
wget $Link -O - | zstd -cd | tar xf -
```

### multithreaded download

```bash
aria2c -s4 -x4 -k1024M $Link -o $save_path
zstd -cd $save_path | tar xf -
openssl sha256 $save_path # checksum verification, optional
```

### download in parts

```bash
mkdir parts && cd parts
wget $List -O url.list
aria2c -s4 -x4 -k1024M -i url.list # multithreaded download
## or
# wget -i url.list
## checksum verification, optional
# cat erigon.$TYPE.$BLOCK.tar.zst.part_* | openssl sha256
## if checksum is not matched, try to check parts one by one
## you can get checksum of parts from list/erigon_$TYPE.sha256
cat erigon.$TYPE.$BLOCK.tar.zst.part_* | zstd -cd | tar xf -
```

[Back to TOC](#bsc-snapshots)
