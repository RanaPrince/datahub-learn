We must check our account balance to make sure we have sufficient **SOL** to perform a transfer. The `getBalance()` function takes a `publicKey` as input and will return the balance associated with that `publicKey`, if there is any.

----------------------------------

# The challenge

{% hint style="tip" %}
In `pages/api/solana/balance.ts`, implement `publicKey` & `balance`.
{% endhint %}

**Take a few minutes to figure this out**

```typescript
//...
    const address = req.body.address as PublicKey;
    const url = getSafeUrl();
    const connection = new Connection(url, "confirmed");
    const publicKey = undefined;
    const balance = undefined;
    res.status(200).json(balance);
//...
```

**Need some help?** Here are a few hints
* [Read about getBalance](https://solana-labs.github.io/solana-web3.js/classes/Connection.html#getbalance)
* [Create a publicKey from a string](https://solana-labs.github.io/solana-web3.js/classes/PublicKey.html#constructor)  

{% hint style="info" %}
You can also [**join us on Discord**](https://discord.gg/fszyM7K) if you have questions.
{% endhint %}

Still not sure how to do this? No problem! The solution is below so you don't get stuck.

----------------------------------

# The solution

```typescript
//...
    const address = req.body.address as PublicKey;
    const url = getSafeUrl();
    const connection = new Connection(url);
    const publicKey = new PublicKey(address);
    const balance = await connection.getBalance(publicKey);
    res.status(200).json(balance);
//...
```

**What happened in the code above?**

* We created an instance of the `PublicKey` using the string formatted address
* Call `connection.getBalance` with that `publicKey`
* Be aware than the balance is denominated in `LAMPORTS`. Remember, `console.log` is your friend 😁  

----------------------------------

# Make sure it works

* Save the code (Next.js will automatically rebuild the page)
* Enter the address you just funded
* Click on **Check Balance**

![](../../../.gitbook/assets/solana-balance-v3.gif)

----------------------------------

# Next

Now that we have an account that has been funded with **SOL** tokens, we are ready to make a transfer to another account!
