# Codama Challenge Notes

## Versions

anchor-cli 1.1.2 · Node.js v24.14.1 · solana-cli 3.1.10 · @codama/cli 1.6.3

## TODO 3

Required accounts: `fundraiser` and `vault`. Optional accounts: `contributorAccount`, `contributorAta`, `tokenProgram`, and `systemProgram`. In `contribute`, deriving `fundraiser` would require `fundraiser.maker` from inside the account being found, while deriving `vault` requires `fundraiser.mint_to_raise`, another field the generated builder does not fetch, so the caller must supply both addresses. In `initialize`, `maker` is an explicit account, allowing Codama to derive `fundraiser` from `maker.key()` and make it optional.

## Bonus

Completed. The Codama-built instruction is converted to a web3.js instruction, sent through the Anchor provider, and verified by checking that the vault balance increases by exactly the contribution amount.

## One thing that surprised me

Whether Codama can derive the same PDA depends on the accounts and seed values exposed by each instruction, not only on the PDA itself.
