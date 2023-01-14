# Limit-Sniper-V3

<img src="https://user-images.githubusercontent.com/70858574/210904846-a055fd00-0e15-4651-90e0-eefb4ec15264.png" width="600">



&nbsp;

# How can I buy it?
Join our Telegram channel for more infos:  https://t.me/LimitSwap 

&nbsp;

# Bot configuration

#### BUY / SELL  PARAMETERS
```toml
[parameters]
# Available values: uniswap / pancakeswap / uniswaptestnet / pancakeswaptestnet
exchange = "uniswap"
api_key = "" # Create an account on Etherscan or BSCscan, get your API key in your account settings, and enter it here

[parameters.buy_amount]
kind = "base" # enter "base" to buy a fixed amount of ETH/BNB / or "tokens" to buy a fixed amount of tokens
in_base = "0.001" # used if kind == base --> enter the ETH/BNB buy amount you want to use
in_tokens = "200000000000000000" # used if kind == tokens --> enter the amount of tokens you want to buy. READ CAREFULLY : this amount will be divided by tokens decimals --> 2000000000000000000 = 2 tokens if decimals = 18
amount_of_spam_tx = 1 # number of txs to send in a row, to be sure not to frontrun liquidity. If you use custom contract, only 1 tx will succeed.

# Sells automatically `amount`% of tokens after `profit`% of profit if the current gas price is less than `max_gas`.
[parameters.auto_sell]
enabled = false
profit = 200 # percentage points; automatically sell the token when price has reached buyprice * this value
amount = 100 # percentage points out of 100; sell this amount of tokens
max_gas = 100 # gwei

[parameters.custom_contract]
enabled = false
address = "" # Enter here the contract address that you got after deploying the contract
same_tx_buys = 1 # number of buys to do in the each transaction
use_multiple_wallets = false # set to false to use the main wallet (trading_address) or to true to use the following wallets as recipients.
wallets = [
  "0x1111111111111111111111111111111111111111",
  "0x2222222222222222222222222222222222222222",
]
```
&nbsp;

&nbsp;

# Examples of Tx with MULTIBUY modes (with custom contract only)

```toml
// Send 5 buys made in tokens to your trading wallet
KIND_OF_SWAP = "base"
in_base = "0.0001"
amount_of_spam_tx = 5
use_multiple_wallets = false
```
<img width="734" alt="image" src="https://user-images.githubusercontent.com/70858574/195204453-e45f313f-29ad-461b-a0fb-13c661367f5a.png">


```toml
// Send 5 buys made in WBNB to your trading wallet
KIND_OF_SWAP = "tokens"
in_base = "1000"
amount_of_spam_tx = 5
use_multiple_wallets = false
```
<img width="723" alt="image" src="https://user-images.githubusercontent.com/70858574/195205348-eae4e2ce-1d9e-4722-a12d-acb05cde5ad4.png">


```toml
// Send 3 buys made in WBNB to 3 different wallets
KIND_OF_SWAP = "base"
in_base = "0.0001"
same_tx_buys = 3
use_multiple_wallets = true
wallets = ["0x200E4Fe41faF92C96bd74c711738Ad550175A779", "0x5aa376af6a5d99d051c3f994de26bb5ae234da26", "0xf62803b9f8a146d07b993ad08bda8de91dde8690"],
```
![image](https://user-images.githubusercontent.com/70858574/195206368-a3049377-354f-40f4-b667-40732514f89e.png)


```toml
// Sent 3 buys made in tokens to 3 different wallets
KIND_OF_SWAP = "tokens"
in_tokens = "1000000000000000000000"
same_tx_buys = 3
use_multiple_wallets = true
wallets = ["0x200E4Fe41faF92C96bd74c711738Ad550175A779", "0x5aa376af6a5d99d051c3f994de26bb5ae234da26", "0xf62803b9f8a146d07b993ad08bda8de91dde8690"],
```
![image](https://user-images.githubusercontent.com/70858574/195205954-a0c44fd1-2717-49a4-b590-a5135622b424.png)

&nbsp;

Example : 
![image](https://user-images.githubusercontent.com/70858574/212440761-b48a0f93-5d36-4bfa-b6bf-bd23b79db072.png)

