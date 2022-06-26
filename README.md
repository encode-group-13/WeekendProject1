# Encode Weekend 1 Projec

Contract address: `0x600f8F0e3F7bB5f28C5694013cE71D02eF5A2d3C`

## Scripts

### Query voting results

Should return 1
`yarn ts-node scripts/Ballot/queryVotingResult.ts 0x600f8F0e3F7bB5f28C5694013cE71D02eF5A2d3C 1`

Should return 0
`yarn ts-node scripts/Ballot/queryVotingResult.ts 0x600f8F0e3F7bB5f28C5694013cE71D02eF5A2d3C 1`

### Query proposals

Should print out all of the proposals of this contract
`yarn ts-node scripts/Ballot/queryProposals.ts 0x600f8F0e3F7bB5f28C5694013cE71D02eF5A2d3C`

### Cast a vote

Should cast a vote with a voter who hasn't already voted:
`yarn ts-node scripts/Ballot/castVote.ts 0x600f8F0e3F7bB5f28C5694013cE71D02eF5A2d3C 1`

Should break, because proposal 77 doesn't exist
`yarn ts-node scripts/Ballot/castVote.ts 0x600f8F0e3F7bB5f28C5694013cE71D02eF5A2d3C 77`

### Give voting rights

Should break, because the voting rights have already been given to this account - giving them to a new account works 👍 
`yarn ts-node scripts/Ballot/giveVotingRights.ts 0x600f8F0e3F7bB5f28C5694013cE71D02eF5A2d3C 0x81b7E08F65Bdf5648606c89998A9CC8164397647`

### Delegate vote

This for some reason doesn't work. I made sure to give the voting rights to a particular address and only then delegate the vote of the caller address.
I get the `Error: cannot estimate gas; transaction may fail or may require manual gas limit error`.
`yarn ts-node scripts/Ballot/delegateVote.ts 0x600f8F0e3F7bB5f28C5694013cE71D02eF5A2d3C 0xD89ffDef0d21c3E03A6AF09Aa31695B6e0414c31`



# Advanced Sample Hardhat Project

This project demonstrates an advanced Hardhat use case, integrating other tools commonly used alongside Hardhat in the ecosystem.

The project comes with a sample contract, a test for that contract, a sample script that deploys that contract, and an example of a task implementation, which simply lists the available accounts. It also comes with a variety of other tools, preconfigured to work with the project code.

Try running some of the following tasks:

```shell
npx hardhat accounts
npx hardhat compile
npx hardhat clean
npx hardhat test
npx hardhat node
npx hardhat help
REPORT_GAS=true npx hardhat test
npx hardhat coverage
npx hardhat run scripts/deploy.ts
TS_NODE_FILES=true npx ts-node scripts/deploy.ts
npx eslint '**/*.{js,ts}'
npx eslint '**/*.{js,ts}' --fix
npx prettier '**/*.{json,sol,md}' --check
npx prettier '**/*.{json,sol,md}' --write
npx solhint 'contracts/**/*.sol'
npx solhint 'contracts/**/*.sol' --fix
```

# Etherscan verification

To try out Etherscan verification, you first need to deploy a contract to an Ethereum network that's supported by Etherscan, such as Ropsten.

In this project, copy the .env.example file to a file named .env, and then edit it to fill in the details. Enter your Etherscan API key, your Ropsten node URL (eg from Alchemy), and the private key of the account which will send the deployment transaction. With a valid .env file in place, first deploy your contract:

```shell
hardhat run --network ropsten scripts/deploy.ts
```

Then, copy the deployment address and paste it in to replace `DEPLOYED_CONTRACT_ADDRESS` in this command:

```shell
npx hardhat verify --network ropsten DEPLOYED_CONTRACT_ADDRESS "Hello, Hardhat!"
```

# Performance optimizations

For faster runs of your tests and scripts, consider skipping ts-node's type checking by setting the environment variable `TS_NODE_TRANSPILE_ONLY` to `1` in hardhat's environment. For more details see [the documentation](https://hardhat.org/guides/typescript.html#performance-optimizations).
