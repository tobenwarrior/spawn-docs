# Transparency and accounting

## What players should be able to check

Spawn's transparency direction is to expose understandable public information and provide data that others can independently analyze. That includes public creator identities, published games, token contract details and dated reports comparing custody assets with recorded obligations.

The local prototype starts with public profiles, people search and a transparency API. Financial fields are unavailable because the ledger and chain integration do not yet exist. Showing no data is different from showing a verified zero.

## Profiles and financial reporting serve different purposes

Public profiles can help players identify creators and see published work. Players choose whether their profile is public and whether a verified wallet link is shown. Private Google identity data is not part of the public profile.

Adding up public profiles cannot prove reserve coverage: private accounts, creator balances, pending withdrawals and other obligations could be missing. Public search is a discovery service, not a complete account ledger or a financial snapshot. Wallet balances outside the custody contract must not be counted as platform reserves.

The proposed financial report must account for all liabilities, including private accounts, without requiring everyone to publish their personal activity. The privacy-preserving proof design has not been selected.

## The proposed reconciliation model

For a single token, the report should compare amounts in the token's smallest integer unit:

**Coverage difference = eligible custody reserves − total platform liabilities**

Total liabilities must include available balances and amounts reserved for pending withdrawals, without counting the same obligation twice. Treasury-owned funds and liabilities to creators need explicit treatment. Different tokens cannot be added as if they were the same unit.

Every report needs a chain identifier, contract addresses, a sufficiently finalized block, a ledger sequence or cutoff and a consistent treatment of transfers in flight. A chain balance from one moment compared with a database total from another can produce a false discrepancy.

A deposit should be credited once after the required confirmation policy. A withdrawal should reserve the account balance, be paid at most once and remain traceable through failure or retry. Reorganizations, duplicates and interrupted processing must be tested.

## Why matching totals is not enough

Matching reserves and liabilities is an accounting check. It does not prove that every balance change was authorized, that all liabilities were disclosed or that privileged operators cannot redirect funds. Fraudulent internal transfers could leave the total unchanged.

If an operator could mint additional tokens, an increased reserve total would not by itself demonstrate sound issuance. Supply controls and administrative transactions must be visible and assessed separately. No mint policy is finalized for Spawn.

The intended assurance model therefore combines reconciliation with an append-only journal, independent verification, restricted permissions, withdrawal controls and public explanations of privileged actions. Backups, monitoring and external review are also required. There is no such thing as an unhackable database.

## Current public interfaces

The transparency endpoint returns the local environment, intended chain, unconfigured token and custody fields, unavailable coverage and an explicit explanation. The snapshots endpoint returns an empty list with an unconfigured status. No signed snapshot or reserve proof is currently produced.

A future implementation should publish independently verifiable snapshots and a verifier that does not depend on trusting the dashboard. The format, publication cadence and privacy model remain to be designed.
