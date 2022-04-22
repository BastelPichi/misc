# SiriCoin rpc docs
  
the base url for the rpc is the mainnet, so `https://siricoin-node-1.dynamic-dns.net:5005`  
The API uses json, you always have a success field (true or false) and a result field, that includes the requested data.  

Theres also a web3 compatible rpc on /web3. Most of the commands should work, however always use the rpc if you can.  
We will provide some web3 examples soon.  

### /ping
returns `Pong!` if the server is up.  
`{"result": "Pong !", "success": true}`

### /stats
returns general coin stat, including difficulty, coin supply and transactions.  
`{  
    "result": {  
        "chain": { "difficulty": 516769783.12022805,  
        "lastBlockHash": "0x00000007f8408de77099debbb1f372731e8f5c203658a035497df57860dc1d88",  
        "length": 3202, "target": "0x84fa991e061b180000000000000000000000000000000000000000000" },  
        "coin": { "holders": 52, "supply": 160160, "transactions": 3317 }  
    },  
    "success": true  
}`  

### /get/transactions
Get all transactions. Very long data, avoid using this endpoint, instead use the following fourendpoints.

### /get/nFirstTxs/n
Get n first transactions.

### /get/nLastTxs/n
Get n last transactions.

### /get/txsByBounds/upperBound/lowerBound
Get transactions between upperBound and lowerBound (in index)

### /get/txIndex/index
Get transaction by index.

### /get/transaction/txhash
Show information about transaction. Only working for block transactions.

### /get/transactions/txhashes
Same as above, but multiple tx hashes seperated by a comma (",").

### /accounts/accountInfo/address
Show balance and block transactions of a address.

### /accounts/sent/address
Show transactions of address

### /accounts/accountBalance/address
Returns balance of address

### /accountstxCilds/tx
Returns childs of a transaction

### /send/rawtransaction
Send a raw, signed, hex encoded transaction in json format, for the node to process.

### /send/buildTransaction
BROKEN! Build an sign a transaction. Requires following GET parameter:  
`privkey -private key  
from  
to  
value - amount`  
BE CAREFUL WITH YOUR PRIVATE KEY! WHO OWNS THE PRIVATE KEY, OWNS THE COINS! Make shure to only send this via a encrypted connection ("https").  

### /chain/block/blockindex
Get information about block (hash, miner, index, time, proof).

### /chain/blockByHash/blockhash
Get block by hash (hash, miner, index, time, proof).

### /chain/getlastblock
Get last block (hash, miner, index, time, proof).

### /chain/miningInfo
Get diff, lastblockhash, target.

### /chain/length
Get length of chain

### /net/getPeers
BROKEN! Get peers.

### /net/getOnlinePeers
BROKEN! Get online peers.
