Bitnewcoin integration/staging tree
================================

http://www.bitnewcoin.com

Copyright (c) 2009-2014 Bitcoin Developers
Copyright (c) 2017-2018 Bitnewcoin Developers

What is Bitnewcoin?
----------------

Bitnewcoin is a lite version of Bitcoin using scrypt as a proof-of-work algorithm.
 - 2.5 minute block targets
 - subsidy halves in 840k blocks (~4 years)
 - ~84 million total coins

The rest is the same as Bitcoin.
 - 50 coins per block
 - 2016 blocks to retarget difficulty

For more information, as well as an immediately useable, binary version of
the Bitnewcoin client sofware, see http://www.bitnewcoin.com.

License
-------

Bitnewcoin is released under the terms of the MIT license. See `COPYING` for more
information or see http://opensource.org/licenses/MIT.

<strong>Begin build for ubuntu</strong> 

Dependencies:
 
<code>sudo apt-get install git -y</code>
 
<code>sudo apt-get install build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils -y</code>
 
<code>sudo apt-get install libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-program-options-dev libboost-test-dev libboost-thread-dev -y</code>
 
<code>sudo apt-get install libboost-all-dev -y</code>
 
<code>sudo apt-get install software-properties-common -y</code>
 
<code>sudo add-apt-repository ppa:bitcoin/bitcoin</code>
 
<code>sudo apt-get update</code>
 
<code>sudo apt-get install libdb4.8-dev libdb4.8++-dev -y</code>
 
<code>sudo apt-get install libminiupnpc-dev -y</code>
 
<code>sudo apt-get install libzmq3-dev -y</code>
 
<code>sudo apt-get install libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler y</code>
 
<code>sudo apt-get install libqt4-dev libprotobuf-dev protobuf-compiler -y</code>

Build daemon

<code>cd src/</code>

<code>make -f makefile.unix</code>

Done, it should generate the bitnewcoind file inside the <code>src/</code> folder


<code>qmake && make</code>

Once you have done this, you can use your wallet, just use the following command:

<code>./bitnewcoin-qt</code>



Development process
-------------------

Developers work in their own trees, then submit pull requests when they think
their feature or bug fix is ready.

If it is a simple/trivial/non-controversial change, then one of the Bitnewcoin
development team members simply pulls it.

If it is a *more complicated or potentially controversial* change, then the patch
submitter will be asked to start a discussion with the devs and community.

The patch will be accepted if there is broad consensus that it is a good thing.
Developers should expect to rework and resubmit patches if the code doesn't
match the project's coding conventions (see `doc/coding.txt`) or are
controversial.

The `master` branch is regularly built and tested, but is not guaranteed to be
completely stable. [Tags](https://github.com/cosmo9able/bitnewcoin/tags) are created
regularly to indicate new official, stable release versions of Bitnewcoin.

Testing
-------

Testing and code review is the bottleneck for development; we get more pull
requests than we can review and test. Please be patient and help out, and
remember this is a security-critical project where any mistake might cost people
lots of money.

### Automated Testing

Developers are strongly encouraged to write unit tests for new code, and to
submit new unit tests for old code.

Unit tests for the core code are in `src/test/`. To compile and run them:

    cd src; make -f makefile.unix test

Unit tests for the GUI code are in `src/qt/test/`. To compile and run them:

    qmake BITCOIN_QT_TEST=1 -o Makefile.test bitcoin-qt.pro
    make -f Makefile.test
    ./bitnewcoin-qt_test
