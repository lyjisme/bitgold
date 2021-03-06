BitGold Project
=====================================

[![Build Status](https://travis-ci.org/bitbaba/bitgold.svg?branch=master)](https://travis-ci.org/bitbaba/bitgold)

What is BitGold?
----------------

BitGold [BGD] is an new digital gold that enables instant payments to
anyone, anywhere in the world. BitGold uses peer-to-peer technology to operate
with no central authority: managing transactions and issuing money are carried
out collectively by the network. BitGold is the name of open source
software which enables the use of this currency. 
see [Features](https://github.com/bitbaba/bitgold/blob/master/README.md#features)
and [RoadMaps](https://github.com/bitbaba/bitgold/blob/master/README.md#roadmaps).

For more information, as well as an immediately useable, binary version of
the BitGold software, see https://bintray.bitbaba.com/bintray/bitgold, or read the
[bitgold design](http://blog.csdn.net/hacode/article/details/78369398) and
[bitcoin original whitepaper](https://bitcoincore.org/bitcoin.pdf).


License
-------

BitGold[BGD] is released under the terms of the MIT license.

See [COPYING](COPYING) for more information or see https://opensource.org/licenses/MIT.

Downloads
-------------

- [Win32 Wallet](https://bintray.bitbaba.com/bitgold/bitgold-win32.tar.gz)
- [Ubuntu Wallet](https://bintray.bitbaba.com/bitgold/bitgold-ubuntu64.tar.gz)
- [Mac Wallet](https://bintray.bitbaba.com/bitgold/bitgold-mac.tar.gz)
- [pre-built miner for windows](https://bintray.bitbaba.com/bitgold/bitgold-miner.zip)

Services
----------------

- [Pool](https://pool.bitbaba.com/)

- [source of Miner](https://github.com/bitbaba/cpuminer)

- [Explorer](https://bitgold.bitbaba.com/)

- [Exchange1](https://vipzbt.com/Trade/index/market/bgd_cny)

- [Exchange2](https://ex.bitbaba.com/)

Features
--------

- 5 minutes per block
- 2-Mega-bytes serialized block size(2x of bitcoin core)
- 42,000,000 coins in PoW stage
- Seg-Witness
- GoldHash as PoW (now SHA256Q, asic-resistant)
- Miner-inside GUI wallet

Roadmaps
----------------

- Support chainstate retrieving in script stack machine
  - nonceOf(height) [example: use nonce to gamble](./doc/gamble.md)
  - hashOf(height)
  - timeOf(height)

- Support non-standard sub-script of P2SH

- Support state storage of non-utxo data

- Support Tx comments(e.g. "pay for coffe")

- Support Instant Messenaging Chat

- Support Mounting of Turing-complete VM for smart contract

Mining 
-------------------
- Pool

```
./minerd --algo=sha256q \
         --threads=1 \
         --url=stratum+tcp://pool.bitbaba.com:3333 \
         --no-getwork \
         --no-gbt \
         --user=GZmKHp12bDUiDCkvvzyZzytwRcNaW3viDM \
         --pass=x \
         --debug \
         --protocol-dump
```

- GBT(GetBlockTemplate) on remote rpc

```
./minerd --algo=sha256q \
	 --threads=1 \
	 --coinbase-sig="bitbaba" \
	 --coinbase-addr=GZmKHp12bDUiDCkvvzyZzytwRcNaW3viDM \
	 --url=http://api.bitbaba.com/ \
	 --no-getwork \
	 --user=rpcuser \
	 --pass=rpcpassword \
	 --debug \
	 --protocol-dump
```

- Solo-Mining Locally

mine.sh

```
while true; 
    do ./bitgold-cli generatetoaddress 1 GZmKHp12bDUiDCkvvzyZzytwRcNaW3viDM 10000000; 
done
```

mine.bat

```
@echo off
:restart

echo minging...

bitgold-cli generatetoaddress 1 GZmKHp12bDUiDCkvvzyZzytwRcNaW3viDM 10000000

ping -w 1 -n 5 1.0.0.1

goto :restart
```

>Note: remember to configure bitgold.conf as following:

```
server=1
rpcuser=rpcuser
rpcpassword=rpcpassword
```

Building from sources
------------------

As you known, the .travis.yml is used for automated building. 
Here is a localized script called *travis.sh*, which can be used 
to build bitgold on your local laptop.

Example Usage:

```
$>mkdir -p ~/home/user1/tarballs; \
$>ln -s ~/home/user1/tarballs depends/sources; \
$>mkdir -p depends/sdk-sources depends/SDKs; \
$>sudo apt-get update; \
$>sh travis.sh;
```

>Note: *~/home/user1/tarballs* is used to cache locale source tarballs of depends.

