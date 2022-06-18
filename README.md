# GenesisH0
Python 3 script for creating the parameters required for a unique SHA256 microcurrency genesis block.


### Options
    Usage: genesis.py [options]
    
    Options:
      -h, --help            show this help message and exit
      -t TIME, --time=TIME  the (unix) time when the genesisblock is created
      -z TIMESTAMP, --timestamp=TIMESTAMP
                            the pszTimestamp found in the coinbase of the
                            genesisblock
      -n NONCE, --nonce=NONCE
                            the first value of the nonce that will be incremented
                            when searching the genesis hash
      -p PUBKEY, --pubkey=PUBKEY
                            the pubkey found in the output script
      -v VALUE, --value=VALUE
                            the value in coins for the output, full value (exp. in
                            bitcoin 5000000000 - To get other coins value: Block
                            Value * 100000000)
      -b BITS, --bits=BITS
                            the target in compact representation, associated to a
                            difficulty of 1


### Defaults
    -t (time)       = int(time.time())
    -z (timestamp)  = "The Times 03/Jan/2009 Chancellor on brink of second bailout for banks"
    -n (nonce)      = 0
    -p (pubkey)     = "04678afdb0fe5548271967f1a67130b7105cd6a828e03909a67962e0ea1f61deb649f6bc3f4cef38c4f35504e51ec112de5c384df7ba0b8d578a4c702b6bf11d5f"
    -v (value)      = 5000000000
    -b (bits)       = 0x1d00ffff


### Examples
Create the original genesis hash found in Bitcoin
    
    python genesis.py -t 1231006505 -n 2083236893
    
    output: 
        algorithm: SHA256
        merkle hash: 4a5e1e4baab89f3a32518a88c31bc87f618f76673e2cc77ab2127b7afdeda33b
        pszTimestamp: The Times 03/Jan/2009 Chancellor on brink of second bailout for banks
        pubkey: 04678afdb0fe5548271967f1a67130b7105cd6a828e03909a67962e0ea1f61deb649f6bc3f4cef38c4f35504e51ec112de5c384df7ba0b8d578a4c702b6bf11d5f
        time: 1231006505
        bits: 0x1d00ffff
        nonce: 2083236893
        Genesis Hash: 000000000019d6689c085ae165831e934ff763ae46a2a6c172b3f1b60a8ce26f

Create a new microcurrency genesis hash (e.g. Arizona)
    
    python genesis.py -z "Arizona Republic Jun/17/2022 Diamondbacks use long ball, small ball to thump Twins in series opener" -t 1655529247 -n 2140992447
    
    output: 
        algorithm: SHA256
        merkle hash: 68ddfae438d132fc0dbab33ec4cad19a0f6c3c86232db68d8a3118aa183fc484
        pszTimestamp: Arizona Republic Jun/17/2022 Diamondbacks use long ball, small ball to thump Twins in series opener
        pubkey: 04678afdb0fe5548271967f1a67130b7105cd6a828e03909a67962e0ea1f61deb649f6bc3f4cef38c4f35504e51ec112de5c384df7ba0b8d578a4c702b6bf11d5f
        time: 1655529247
        bits: 0x1d00ffff
        nonce: 2140992447
        Genesis Hash: 00000000facf945f95ad68d109d4af6e1557c6107b4ae6ff399af498fa765da1


### Running on Debian
Recommended to initial multiple instances simultaneously to find a new genesis faster    
    
    sudo apt-get -y install git-core
    git clone https://github.com/satoshiware/genesis.git ~/genesis
    cd ~/genesis
    python3 genesis.py -z "Local newspaper of the day TODAY'S DATE Something intersting that happened"