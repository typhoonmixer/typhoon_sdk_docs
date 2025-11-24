# Private Transfer Example


``` javascript
import { TyphoonSDK } from 'typhoon-sdk'
import { RpcProvider, Account } from 'starknet';

const provider = new RpcProvider({ nodeUrl: "https://starknet-mainnet.public.blastapi.io/rpc/v0_8" });
const sdk = new TyphoonSDK()
const STRK_ADDR = "0x04718f5a0fc34cc1af16a1cdee98ffb20c31f5cd61d6ab07201858f4287c938d"
const amount = 110000000000000000000n // 110 STRK

// use the wallet account if you run in your frontend
const account = new Account(provider, "0xyouraddress", "0xprivkey"); 

// this function generates the calls to make a deposit
let calls = await sdk.generate_approve_and_deposit_calls(amount, STRK_ADDR)

// execute the deposit calls
const multiCall = await account.execute(calls);
await account.waitForTransaction(multiCall.transaction_hash);

await download_notes(multiCall.transaction_hash)

// withdraw your deposited funds to the address in the recipient list
// withdraw has two arguments the txhash of the deposit execution and a list of recipients 
await sdk.withdraw(multiCall.transaction_hash, ['0xrecipientAddress']) 

```