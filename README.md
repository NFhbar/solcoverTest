# Solidity Coverage Test

Possible incorrect behavior in [solidity-coverage](https://github.com/sc-forks/solidity-coverage) with new solidity constructor [rules](https://github.com/ethereum/solidity/releases/tag/v0.4.22):

> Constructors should now be defined using constructor(uint arg1, uint arg2) { ... } to make them stand out and avoid bugs when contracts are renamed but not their constructors.

## Local test

clone:
```

```

install:
```
$ npm install
```

run coverage:
```
$ npm run coverage
```

it will fail because constructor in ```Ballot.sol``` is defined as constructor. Stop ganache:
```
$ npm run stop
```

Change constructor back to old definition. In ```Ballot.sol``` line 20, change:
```
constructor(uint8 _numProposals)
```

to:
```
function Ballot(uint8 _numProposals)
```

run coverage again:
```
npm run coverage
```

it complains:
```
Warning: Defining constructors as functions with the same name as the contract is deprecated. Use "constructor(...) { ... }" instead.
    function Ballot(uint8 _numProposals) public {
    ^ (Relevant source part starts here and spans across multiple lines).
```
but finishes correctly.
