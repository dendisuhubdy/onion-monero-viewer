# Onion Monero Viewer

Currently, there is not possible to search for transactions in Monero Blockchain
online associated with a given address and viewkey. This is a serious problem,
especially for people using paper wallets, since they cant verying if they recived
founds whitch they expect.

In this example, this problem is address by development of an online hiden service
where users can input anonymouskt their address and viewkey to search for
associated transaction. The example not only shows how to use Monero C++ libraries,
 but also demonstrates how to use:

 - [crow](https://github.com/ipkn/crow) - C++ micro web framework
 - [lmdb++](https://github.com/bendiken/lmdbxx) - C++ wrapper for the LMDB
 - [mstch](https://github.com/no1msd/mstch) - C++ {{mustache}} templates
 - [rapidjson](https://github.com/miloyip/rapidjson) - C++ JSON parser/generator


## Temporary Onion address for testing

Tor users:

 - [http://hbyjphgpe6cumkp3.onion](http://hbyjphgpe6cumkp3.onion/)

Non tor users, can try tor proxy, e.g.,

 - [http://dont-know-yet.onion](http://dont-know-yet.onion.onion.to)

## Still under development

The Onion Monero Viewer is still under development and testing.
So not everything can work as expected and the viewer can be offline from time
to time, when changes are being made to it.

## Onion Monero Viewer features

The key features of the Onion Monero Viewer are:

 - available as a hidden service,
 - no web analytics trackers, no images, co cookies
 - open sourced,
 - made fully in C++,

## Prerequisite

Everything here was done and tested using Monero 0.9.4 on Ubuntu 16.04 x86_64.

Instruction for Monero 0.9 compilation and Monero headers and libraries setup are
as shown here:
 - [Compile Monero 0.9 on Ubuntu 16.04 x64](https://github.com/moneroexamples/compile-monero-09-on-ubuntu-16-04)
 - [lmdbcpp-monero](https://github.com/moneroexamples/lmdbcpp-monero.git)

## C++ code

```c++

```

## Example screenshot

### Front page
![Onion Monero Viewer](https://raw.githubusercontent.com/moneroexamples/onion-monero-viewer/master/screenshot/screenshot2.jpg)

### Results page
![Onion Monero Viewer](https://raw.githubusercontent.com/moneroexamples/onion-monero-viewer/master/screenshot/screenshot3.jpg)


## Compile and run the viewer

##### Monero headers and libraries setup

The Onion Explorer uses Monero C++ libraries and headers. Also some functionality
 in the Explorer for mempool is achieved through [patching](https://github.com/moneroexamples/compile-monero-09-on-ubuntu-16-04/blob/master/res/tx_blob_to_tx_info.patch)
 the Monero deamon.
 Instructions how to download Monero source files, apply a patch, compile  Monero,
 setup header and library files are presented here:

- https://github.com/moneroexamples/compile-monero-09-on-ubuntu-16-04 (Ubuntu 16.04)
- https://github.com/moneroexamples/compile-monero-09-on-arch-linux (Arch Linux)


##### Custom lmdb database (optional)

Most unique search abilities of the Onion Viewer are achieved through using
a [custom lmdb database](https://github.com/moneroexamples/lmdbcpp-monero.git) constructed based on the Monero blockchain.
The reason for the custom database is that Monero's own lmdb database has limited
search abilities.

Instruction how to compile the `lmdbcpp-monero` are provided here:

 - https://github.com/moneroexamples/lmdbcpp-monero.git

The custom database is rather big, 12GB now, and it must be running alongside Monero deamon
 so that it keeps updating itself with new information from new blocks as they are added
  to the blockchain.

For these reasons, its use is optional. However, without it, some searches wont be possible,
e.g., searching for key images, output and tx public keys, encrypted payments id.


##### Compile and run the viewer
Once the Monero is compiled and setup, the viewer can be downloaded and compiled
as follows:

```bash
# download the source code
git clone https://github.com/moneroexamples/onion-monero-viewer.git

# enter the downloaded sourced code folder
cd onion-monero-viewer

# create the makefile
cmake .

# compile
make
```

When compilation finishes executable `xmrviewer` should be created.

To run it:
```
./xmrviewer
```

Example output:

```bash
[mwo@arch onion-monero-viewer]$ ./xmrviewer
2016-May-28 10:04:49.160280 Blockchain initialized. last block: 1056761, d0.h0.m12.s47 time ago, current difficulty: 1517857750
(2016-05-28 02:04:49) [INFO    ] Crow/0.1 server is running, local port 8081
```

Go to your browser: http://127.0.0.1:8081

## Testing address and viewkey

For testing of the viewer, one can use [official address and viewkey](https://github.com/monero-project/bitmonero#supporting-the-project)
of the Monero, i.e.,

- Address: 44AFFq5kSiGBoZ4NMDwYtN18obc8AemS33DBLWs3H7otXft3XjrpDtQGv7SqSsaBYBb98uNbr2VBBEt7f2wfn3RVGQBEP3A
- Viewkey: f359631075708155cc3d92a32b75a7d02a5dcf27756707b47a2b31b21c389501

Monero [forum donation](https://www.reddit.com/r/Monero/comments/5j2rm7/in_last_four_weekes_there_were_about_850_xmr/dbdmzt7/?context=3),

- Address: 45ttEikQEZWN1m7VxaVN9rjQkpSdmpGZ82GwUps66neQ1PqbQMno4wMY8F5jiDt2GoHzCtMwa7PDPJUJYb1GYrMP4CwAwNp
- Viewkey: c9347bc1e101eab46d3a6532c5b6066e925f499b47d285d5720e6a6f4cc4350c

[Old Monero donation](https://github.com/monero-project/monero/pull/714/files) address:

- Address: 46BeWrHpwXmHDpDEUmZBWZfoQpdc6HaERCNmx1pEYL2rAcuwufPN9rXHHtyUA4QVy66qeFQkn6sfK8aHYjA3jk3o1Bv16em 
- Viewkey: e422831985c9205238ef84daf6805526c14d96fd7b059fe68c7ab98e495e5703


## Other examples

Other examples can be found on  [github](https://github.com/moneroexamples?tab=repositories).
Please know that some of the examples/repositories are not
finished and may not work as intended.

## How can you help?

Constructive criticism, code and website edits are always good. They can be made through github.


