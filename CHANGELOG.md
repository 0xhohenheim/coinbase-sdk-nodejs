# Coinbase Node.js SDK Changelog

## Unreleased

## [0.6.1] - 2024-09-23

### Added
- Export all missing types in `src/index`

## [0.6.0] - 2024-09-18

### Added
- Add `deployToken` method to `WalletAddress` and `Wallet` to deploy an ERC20, updated `SmartContract` class to support deployment and fetching contract details
- Add SOL asset support
- Fix a bug where large numbers were being returned in scientific notation

### Breaking
- `Asset#toAtomicAmount` now returns a BigInt instead of a Decimal

## [0.5.1] - 2024-09-12

### Fixed
- Fixed a bug that blocked arbitrum mainnet wallets from being created

## [0.5.0] - 2024-09-11

- Add Arbitrum-Mainnet support for Native transfers.
- Add `Coinbase.configure` method to allow for configuration of the SDK and marked constructor as deprecated.
- Return correlation ID from APIError response
- Add optional fields to `CreateContractInvocationOptions` to set amount for payable contract method invocations
- Add a `StakingRewardFormat` enum to allow for specifying the format in which staking rewards should be returned.

## [0.4.0] - 2024-09-06

### Changed
- `getDefaultAddress` wallet method updated to return a promise, and `getAddress` wallet methods now return a promise and `WalletAddress` instead of `Address`. Both functions will now fetch addresses for the wallet if they haven't been loaded.

## [0.3.0] - 2024-09-05

### Added

- Add support for list address transactions.
- Add support for exporting the private key of a `WalletAddress`
- Add support for creating arbitrary payload signatures.
- Add support for invoking Smart Contracts using MPC and Developer-managed Wallets.

## [0.2.0]

### Added

- USDC Faucet support on Base Sepolia
- Improved error messages for `InternalError`

## [0.1.1] - 2024-08-27

- Fixed a bug where `listHistoricalBalances` method was parsing conventional ETH balances instead of atomic units

## [0.1.0] - 2024-08-22

### Added

- Add `listHistoricalBalances` wallet method, that lists the historical balances for the wallet's default address.
- Add toAddressId() method to Transaction class

### Removed

- Remove user concept from the SDK
- Remove "pending" status from StakingOperationStatusEnum
- Add staking operation class helper methods like `isTerminalState`, `isFailedState` and `isCompleteState`.
- Add validator status enum

### Changed

- The `createTransfer` and `createTrade` functions no longer wait for the transactions to confirm or
  fail on-chain.
  - Now they return a `Transfer` and `Trade` object respectively, which support the `wait`
    function, e.g. `await transfer.wait()`.
  - This ensures that the developer has a reference to the object in case there is a timeout while
    waiting to land on-chain.
- Update `reload()` method to work with both External and Wallet address.
- Update `createStakingOperation` logic to make sure we only pull in newer unsigned txs from the server.
  This is especially important for External Address use-case where tx signing and broadcast status is maintained on client side, and we risk overwriting the existing txs.
- Increase default timeout for `createStakingOperation` to 10 min.

## [0.0.16] - 2024-08-14

### Added

- Add Function `listHistoricalBalances` for `Address` for fetching historical balances for an asset
- Support for retrieving historical staking balances information
- USD value conversion details to the StakingReward object
- Gasless USDC Sends
- Support for Ethereum-Mainnet and Polygon-Mainnet

## [0.0.15] - 2024-08-12

### Changed

- Fixed `Wallet` address hydration for `Wallet.import`

## [0.0.14] - 2024-08-05

### Added

- Support for Shared ETH Staking for Wallet Addresses

### Changed

- `unsigned_payload`, `signed_payload`, `status`, and `transaction_hash` in-line fields on `Transfer` are deprecated in favor of those on `Transaction`

## [0.0.13] - 2024-07-30

### Added

- Support for trade with MPC Server-Signer
- `CreateTradeOptions` type

## [0.0.12] - 2024-07-24

### Changed
- Expose `Validator` class

## [0.0.11] - 2024-07-24

### Changed
- Fixed signer wallets signing flow

## [0.0.10] - 2024-07-23

### Added

- Add support for Dedicated ETH Staking for external addresses
- Add support for listing validator details and fetch details of a specific validator

### Changed
- Improved accessibility for `StakingReward` and `StakingOperation` classes
- Fixed a bug with `StakingOperation.sign` method, where we were not properly waiting on a Promise
- Changed `buildStakeOperation`, `buildUnstakeOperation`, and `buildClaimRewardsOperation` to take `mode` as an explicit parameter optional parameter

## [0.0.9] - 2024-06-26

### Added

- `CreateTransferOptions` type
- Support external addresses for balance fetching and requesting faucet funds.
- Support for building staking operations
- Support for retrieving staking rewards information
- Add support for listing address trades via address.listTrades

## [0.0.8] - 2024-06-18

### Added

- Support assets dynamically from the backend without SDK changes.

## [0.0.7] - 2024-06-11

### Added

- Added Base Mainnet network support
- `ServerSigner` object
- Ability to get default Server-Signer

### Changed

Updated the usage of `Coinbase.networkList` to `Coinbase.networks`

## [0.0.6] - 2024-06-03

### Added

- Ability to create wallets backed by server signers and transfer with them
- Changed save_wallet to save_seed
- Changed load_wallets to load_seed and moved at wallet level

### Changed

- Changed save_wallet to save_seed
- Changed load_wallets to load_seed and moved at wallet level

## [0.0.4] - 2024-05-28

### Added

Initial release of the Coinbase NodeJS.

- Supported networks: Base Sepolia
- Wallet create and import
- Address management
- Send and receive ETH, ETC-20s
- Ability to hydrate wallets
- API Key-based authentication
- API HTTP debugging
- User object and getDefaultUser
- Individual private key export
- Error specifications
