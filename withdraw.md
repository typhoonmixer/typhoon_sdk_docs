# Withdraw
The withdraw function

## Withdraw function
```javascript
await sdk.withdraw(transaction_hash, ['0xADDR']) 
```
The withdraw function receives to arguments, the first one is the transaction hash in which the deposit occurs and the second argument is a list of recipient addresses, this means that you can split your withdraw between a list of recipients in order to improve your privacy, this withdraw is executed by the Typhoon paymaster, so all the network fees are covered and there is no link with the user withdrawing.

## Get withdraw calldata

```javascript
await sdk.get_withdraw_calldata(txhash, receiver_list)
```
This function receives the same arguments from the previous one, but instead of executing the transaction, this function just return the calldata to the withdraw function.
