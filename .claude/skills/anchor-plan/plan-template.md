# Program Plan: [Program Name]

Use bullet points throughout for legibility.

## Overview

- What the program does and why it's being built
- The core problem it solves

## Users & Actors

- Who interacts with the program and in what capacity
- What role does each actor play? (eg. admin, end user, protocol)
- How might these actors interact with the program concurrently?

## Accounts

For each account, provide:

| Account Name | Fields | Types | Size (bytes) | Lifecycle |
|---|---|---|---|---|

- Note any relationships between accounts
- Include const values used for space allocation

## PDAs & Account Contexts

For each PDA, provide:

| PDA Name | Seeds | Bump Strategy | Used In (Instructions) |
|---|---|---|---|

- For each instruction context, list the accounts, constraints,
  and required programs (eg. System Program, Token Program)

## Instructions

For each instruction, provide:

| Instruction | Description | Context | Validations | State Changes | Events |
|---|---|---|---|---|---|

- Note any ordering dependencies between instructions

## Errors

| Error Code | Description | Triggered By |
|---|---|---|

## Access Control & Invariants

- For each instruction, who needs to sign?
- Authority setup and transferability
- Upgrade strategy
- Invariants that must always hold true
