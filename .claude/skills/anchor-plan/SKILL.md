---
name: anchor-plan
description: This skill is for planning and architecting Solana Anchor Programs before writing any code. Use when the user wants to design program structure, define account layouts, map out instruction flows, plan PDA strategies, or think through state management and access control for an Anchor project.
user-invocable: true
allowed-tools: Read, Grep, Glob, WebFetch, WebSearch, AskUserQuestion
argument-hint: "[program-description]"
---
Anchor documentation: https://www.anchor-lang.com/docs
Solana documentation: https://solana.com/docs

Follow this process when planning out Solana Programs with Anchor:

1. Ask the user what is the main purpose of the Program
	- You need to understand the goal or intention of what the user wants to build
	- Analyse what the users response is, go deep on their thinking and ask clarifying questions
	- `AskUserQuestion` can be used here to gain further clarification on their goals and objectives

2. Ask the user who the main users of the Program will be
	- You need to know who will be interacting with the Program so you can understand how to do the overall structure
	- Analyse the user response to see if they have thought of all users of the program, if the user is a beginner they might not fully understand everything
	- Investigate how these users may also affect the Program concurrently, or at least think about this and document it
	- `AskUserQuestion` can be used here to gain further clarification on the users of the Program

3. Define the accounts
	- What states need to be stored?
	- What account structures are needed for the Program?
	- What are their fields and their types?
	- Analyse this against user goals as account space costs rent, `AskUserQuestion` could be used here if required
	- How much space will this account and its values take up?
	- Consider const values that will represent this
	- What is the relationship between accounts? Does one reference the other? Is there a one-to-many relationship?
	- Which accounts are created once and never change? Which get updated frequently?

4. Map out PDAs and derive account structs
	- What accounts need to be PDAs versus keypair accounts?
	- What seeds will uniquely identify each PDA? Prevent collisions here
	- Will bumps be stored in the account or re-derived?
	- Document each PDA with its seeds, eg: User Stake = [b"stake", user, pool]
	- Consider how users of the Program will act on the accounts you have defined
	- For each instruction context, what accounts are needed?
	- What other programs will be needed? Eg. System Program, Token Program
	- What constraints are needed on each account? (has_one, seeds, mut, signer)
	- Who has authority to change state?

5. Design the instructions
	- What can users do within the Program?
	- For each instruction, define:
		- A clear description of what the instruction does
		- What context (accounts, signers, programs) is needed?
		- What validations must pass before the logic runs?
		- What state changes occur? Which accounts are mutated and how?
		- Should an event be emitted for this instruction?
	- Consider the order of operations — do some instructions need to be called before others? (eg. initialize before deposit)
	- What errors should be flagged during the course of an instruction?
	- `AskUserQuestion` to walk through each instruction with the user

6. Define errors that can happen in the program
	- What could potentially go wrong from your understanding of the program?
	- What custom errors are needed in order to catch these?
	- `AskUserQuestion` can be useful here just to double check the logic with the user, and highlight any potential areas that they haven't thought about

7. Access Control
	- For each instruction, who needs to sign the transaction?
	- Are there admin or authority-only instructions? How is the authority set and can it be transferred?
	- Are there any multi-signature requirements?
	- What happens if an unauthorised user attempts to call an instruction?
	- Consider upgrade authority — who can upgrade the program, or should it be immutable?
	- Consider invariants — what conditions must always hold true in the program? For example: balances summing correctly, authority signers matching stored keys, timestamps being sequential, accounts never entering invalid states
	- `AskUserQuestion` to clarify with the user who should have access to what instruction or functionality within the Program

8. Compile the Program Plan
	- Using all the information gathered, produce a complete program plan
	- The most up to date documentation can be found at: https://www.anchor-lang.com/docs
	- This plan should be clear and specific, following the [plan-template.md](plan-template.md)
	- This should be created as a markdown file for the user, which they can use to build out their Program
