# Bits Calculator
Python 3 script for calculating the bits (compact form) for the desired difficulty (or hashrate) of a genesis block.

### Options
    Usage: bits_calculator.py [options]
    
    Options:
      -h, --help            show this help message and exit
      -t TIME, --time=TIME  time between blocks (seconds)
      -r HASHRATE, --hashrate=HASHRATE
                            starting hashrate (h/s)

 parser = OptionParser()
    parser.add_option("-t", "--time", dest="time", default=600, type="int", help="time between blocks (seconds)")
    parser.add_option("-r", "--hashrate", dest="hashrate", default=(2**32)/600, type="int", help="starting hashrate (h/s)")

### Defaults
    -t (time)       = 600 seconds
    -r (hashrate)   = (2**32)/600

### Examples
Create the original genesis hash found in Bitcoin
    
    python bits_calculator.py -t 120 -r $((9.1983 * 1000000000) 

    
    output: 
        algorithm: SHA256
        merkle hash: 4a5e1e4baab89f3a32518a88c31bc87f618f76673e2cc77ab2127b7afdeda33b
        pszTimestamp: The Times 03/Jan/2009 Chancellor on brink of second bailout for banks
        pubkey: 04678afdb0fe5548271967f1a67130b7105cd6a828e03909a67962e0ea1f61deb649f6bc3f4cef38c4f35504e51ec112de5c384df7ba0b8d578a4c702b6bf11d5f
        time: 1231006505
        bits: 0x1d00ffff
        value: 5000000000
      
