# TrxDoge on TRC20
To accomplish this, the TRC20 token operates on the TRON blockchain by encoding the information within the transaction's memo field.


## Token Economic
 - Token: TrxDoge
 - Supply: 2100000000
 - limit: 2000

## Method
 - deploy: `data:,{"p":"trc-20","op":"deploy","tick":"trxdoge","max":"2100000000","lim":"2000"}`
 - mint: `data:,{"p":"trc-20","op":"mint","tick":"trxdoge","amt":"2000"}`
 - transfer: `data:,{"p":"trc-20","op":"transfer","tick":"trxi","detail":[{"to":"TRON Address","amt":"2000"}]}`

## Deploy txid
soon


## Mint TRXI with TokenPocket Wallet
 - Receiver address:TMeMnPnyiaeetnT5J6k2isJc7RdpzQPhV7.
 - Transfer amount 2 TRX
 - Click on Advanced Settings and fill in `data:,{"p":"trc-20","op":"mint","tick":"trxdoge","amt":"2000"}`



## Mint TRXI with nodejs
1. Install Node.js
2. Create a directory,such as `TRC20Mint`
3. Open `TRC20Mint`, execute command:`npm init`
4. Execute command:`npm install tronweb `
5. Create an index.js file,copy the code below
6. Run index.js:`node index.js` 

```
const TronWeb = require('tronweb');
const HttpProvider = TronWeb.providers.HttpProvider;
const fullNode = new HttpProvider("https://api.trongrid.io");
const solidityNode = new HttpProvider("https://api.trongrid.io");
const eventServer = new HttpProvider("https://api.trongrid.io");
const privateKey = "your privateKey"; //
const tronWeb = new TronWeb(fullNode, solidityNode, eventServer, privateKey);

const blackHole = "TMeMnPnyiaeetnT5J6k2isJc7RdpzQPhV7";  //TrxDoge address

const memo = 'data:,{"p":"trc-20","op":"mint","tick":"trxdoge","amt":"2000"}';  

async function main() {

    const unSignedTxn = await tronWeb.transactionBuilder.sendTrx(TMeMnPnyiaeetnT5J6k2isJc7RdpzQPhV7e, 2000000); //2 TRX is the mint fee.
    const unSignedTxnWithNote = await tronWeb.transactionBuilder.addUpdateData(unSignedTxn, memo, 'utf8');
    const signedTxn = await tronWeb.trx.sign(unSignedTxnWithNote);
    console.log("signed =>", signedTxn);
    const ret = await tronWeb.trx.sendRawTransaction(signedTxn);
    console.log("broadcast =>", ret);
}

main().then(() => {

    })
    .catch((err) => {
        console.log("error:", err);
    });
```




## Indexer(TBA)


## FAQ


### Why 2TRX to sending to TMeMnPnyiaeetnT5J6k2isJc7RdpzQPhV7?
This is the mint fee for trxDoge
