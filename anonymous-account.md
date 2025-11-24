# Anonymous Accounts

Typhoon anonymous accounts allows you or your users to access all the Starknet ecosystem in anonymous mode.

Here is a simple example on how to use it in your code:

```javascript
let sdk = new TyphoonSDK();
let depositCalls = await sdk.generate_approve_and_deposit_calls(amount, token_address);
let res = await account.execute(depositCalls);
await provider.waitForTransaction(res.transaction_hash);
await sdk.download_notes(res.transaction_hash);

//get the message to be signed
let tm = sdk.get_typedMessage();

// sign the message
let sig = await account.signMessage(tm);

// this is the text for the genesis private key
let privText = Array.from("head")
  .map((char) => char.charCodeAt(0).toString(16).padStart(2, "0"))
  .join("");

let genPrivKey = hash.computePoseidonHash(
  hash.computePoseidonHash(sig[1], sig[2]),
  BigInt("0x" + privText)
);

// this is the text for the following private keys
let nextText = Array.from("next")
  .map((char) => char.charCodeAt(0).toString(16).padStart(2, "0"))
  .join("");
 
// check if the user already have previous anonymous accounts
let validacc = await sdk.get_valid_anonymous_accounts(
  genPrivKey,
  address,
  connector.id
);
let lastPrivKey = "";

// if there is previous anonymous accounts just add to the end of the queue
if (validacc.length > 0) {
  lastPrivKey = hash.computePoseidonHash(
    BigInt(validacc[validacc.length - 1].privKey),
    BigInt("0x" + nextText)
  );
} else {
  lastPrivKey = genPrivKey;
}

// then just withdraw to the nearly created anonymous accounts
await sdk.withdraw_to_anonymous_account(
  res.transaction_hash,
  lastPrivKey,
  split,
  address,
  connector.id
);
```
