## Safe Pay Tutorial

1. yarn add

2. anchor build

3. anchor test

Note:

- Need to change program id in both Anchor.toml and src/lib.rs

- Owner of an account is a program, only this program can modify data of this account.

- Authority of an account is a pubKey. Who own respective priKey or respective program can sign and create tx to modify data of this account.

# Flow how Alice pay some tokens to Bob through an escrow program.

- Flow 1:

Alice has Token Account.

Alice creates PDA to store state of an escrow -> Escrow State Account (owner is Escrow Program)

Alice creates PDA to receive Alice's token -> Escrow Token Account with authority is Escrow State Account (owner is Token Program)

Alice transfers token to Escrow Token Account and Bob withdraws from this account.

- Flow 2:

Alice has Token Account.

Alice create an Account to store state of an escrow -> Escrow State Account -> Alice own private key of this account (owner is Escrow Program)

Alice creates PDA to receive Alice's token -> Escrow Token Account with authority is Escrow State Account (owner is Token Program)

Alice transfers token to Escrow Token Account and Bob withdraws from this account.

- Flow 3:

Alice has Token Account.

Alice creates PDA to store state of an escrow -> Escrow State Account (owner is Escrow Program)

Alice creates temp token account and set authority is Escrow State Account (owner is Token Program, Alice can do anything although she has priKey of this account)

Alice transfers token to Escrow Token Account and Bob withdraws from this account.
