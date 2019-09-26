1. Seed nodes (src/CryptoNoteConfig.h)

Setup 2 ubuntu servers to act as seed nodes 2gb ram minimum and add IP addresses of seed nodes.

Example:

const std::initializer_list<const char*> SEED_NODES = {
  "111.11.11.11:17236",
  "222.22.22.22:17236",
};

2. Add logic for 10,000,000,000 masque coin premine in src/CryptoNoteConfig.h

3. Build the binaries with a blank genesis tx hex — src/CryptoNoteConfig.h
You should leave const char GENESIS_COINBASE_TX_HEX[] blank and compile the binaries without it.
Example:
const char GENESIS_COINBASE_TX_HEX[] = "";

4. Start the daemon to print out the genesis block
Run your daemon with --print-genesis-tx argument. It will print out the genesis block coinbase transaction hash.
Example:
masquecoind --print-genesis-tx

5. Insert the printed transaction hash — src/CryptoNoteConfig.h
Copy the tx hash that has been printed out by the deamon to GENESIS_COINBASE_TX_HEX in src/CryptoNoteConfig.h
Example:
const char GENESIS_COINBASE_TX_HEX[] = "013c01ff0001ffff...785a33d9ebdba68b0";
Recompile the binaries

p2p Port: 75384
rpc Port: 31545
