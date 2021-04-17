# erc20Token

A Standard Solc Compiled ERC20 for basic contract calls.


## Usage

Import the token like so:

```go
import (
	token "github.com/ricknightcrypto/erc20token"
)
```

Then create an instance of the token and make function calls

```go
import (
	token "github.com/ricknightcrypto/erc20token"
)

func GetCurrentContractBalance() {
	client, err := ethclient.Dial(infura)

	if err != nil {
		log.Fatal(err)
	}

	// Contract Address
	tokenAddress := common.HexToAddress("0xe41d2489571d322189246dafa5ebde1f4699f498")
	instance, err := token.NewToken(tokenAddress, client)

	if err != nil {
		log.Fatal(err)
	}

	// Wallet Address
	address := common.HexToAddress("0xba7f8b5fb1b19c1211c5d49550fcd149177a5eaf")
  
  // Calling BalanceOf function on token instance
	bal, err := instance.BalanceOf(&bind.CallOpts{}, address)
	if err != nil {
		log.Fatal(err)
	}
}
```
