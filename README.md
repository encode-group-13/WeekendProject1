# Encode Weekend 1 Project

Contract address: `0x600f8F0e3F7bB5f28C5694013cE71D02eF5A2d3C`
Explorer: https://docs.google.com/document/d/1G4cjUGiCxfCDDBQYvuzX-GKwl3dALkL362azwYMRyO8

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
