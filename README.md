# blockchain-vote
A voting application demo for codemash

## Hands-on Exercise 1: 

- Get online (CodeMash)
- VM  (http://prereqs.codemash.org/)
- mkdir voting_app
- npm install ethereumjs-testrpc web3@0.20.1
- node_modules/.bin/testrpc
- npm install solc

## Exercise 2.1: Compile Smart Contract
```
> Web3 = require('web3')

> web3 = new Web3(new Web3.providers.HttpProvider("http://localhost:8545"));

> web3.eth.accounts
> code = fs.readFileSync('Voting.sol').toString()
>solc = require('solc')
> compiledCode = solc.compile(code)
```



## Exercise 2.2: Deploy Smart Contract
```
> abiDefinition = JSON.parse(compiledCode.contracts[':Voting'].interface)
> VotingContract = web3.eth.contract(abiDefinition)
> byteCode = compiledCode.contracts[':Voting'].bytecode
```





## Exercise 3: Interacting with contract on console
```
>contractInstance.totalVotesFor.call('Rama')
{ [String: '0'] s: 1, e: 0, c: [ 0 ] }

>contractInstance.voteForCandidate('Rama', {from: web3.eth.accounts[0]})

>contractInstance.totalVotesFor.call('Rama').toLocaleString()
'3'
```
Save the contractInstance.address for next exercise.


## Building a Simple web page
- Clone this repo
- Open Voting.sol and change the contractInstance.address to your own address
- Open index.html on any browser
- Increment votes and play around.

