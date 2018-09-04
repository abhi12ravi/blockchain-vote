# blockchain-vote
A voting application demo for codemash

## Hands-on Exercise 1: 

- Get online (CodeMash)
- VM  (http://prereqs.codemash.org/)
- mkdir voting_app
- If you get an error message `npm update check failed`, run this on terminal - 
  - `sudo chown -R $USER:$(id -gn $USER) /home/<username>/.config`
  - `sudo npm install -g npm`
- `sudo npm install ganache-cli web3@0.20.1`
- node_modules/.bin/testrpc
- npm install solc

## Exercise 2.0: Start a test blockchain network

`$node_modules/.bin/ganache-cli`

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
## Excercise 2.2b: Deploy Smart contract
```
> deployedContract = VotingContract.new(['Rama','Nick','Jose'],{data: byteCode, from: web3.eth.accounts[0], gas: 4700000})
> deployedContract.address
> contractInstance = VotingContract.at(deployedContract.address)

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
- Open index.js and change the contractInstance.address to your own address
- Open index.html on any browser
- Increment votes and play around.


### Truffle and advanced topics:
Part 2: https://medium.com/@mvmurthy/full-stack-hello-world-voting-ethereum-dapp-tutorial-part-2-30b3d335aa1f
