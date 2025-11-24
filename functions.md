# Functions

```javascript
    get_secrets()
```
Return the secrets stored in the TyphoonSDK instance, this will only return data after you call generate_approve_and_deposit_calls function.


```javascript
    set_secrets(new_secrets)
```
Set the secrets stored in your TyphoonSDK instance.


```javascript
    get_nullifiers()
```
Return the nulifiers stored in the TyphoonSDK instance, this will only return data after you call generate_approve_and_deposit_calls function.


```javascript
    set_nullifiers(new_nullifiers)
```
Set the nullifiers stored in your TyphoonSDK instance.


```javascript
    get_pools()
```
Return the pools stored in the TyphoonSDK instance, this will only return data after you call generate_approve_and_deposit_calls function.


```javascript
    set_pools(new_pools)
```
Set the pools stored in your TyphoonSDK instance.


```javascript
    async get_token_minimal_amount(token_address)
```
This function returns the minimal amount required by Typhoon to mix the tokens (normally is a very small amount).


```javascript
    init(secrets, nullifiers, pools)
```
This function sets the secrets, nullifiers and pools values.


```javascript
    get_typedMessage()
```
Return the message that is signed to generate a anonymous account.


```javascript
    async withdraw_fee_by_token(token_address)
```
Return the withdraw fee for the pools of an specific token.


```javascript
    async get_compliance_data(secret, nullifier, txhash, pool)
```
Return all the data needed for compliance.


```javascript
    async download_notes(txhash)
```
Download the secret data in a note format (works in web and desktop scripts).

```javascript
    async generate_approve_and_deposit_calls(amount, token_address)
```
Generate the approve and deposit calls for the user to execute.

```javascript
    async get_withdraw_calldata(txhash, receiver_list)
```
Generate and return the calldata for the ones who want to make the withdraw manually.

```javascript
    async withdraw(txhash, receiver_list)
```
Withdraw the notes for a given list of receivers

```javascript
    async withdraw_to_anonymous_account(txhash, lastAnonPrivKey, splited, address, accountid)
```
Withdraw the notes to an anonymous account.

```javascript
    async get_valid_anonymous_accounts(genPrivKey, address, accountid) 
```
Get all anonymous accounts for a given genPrivKey.
