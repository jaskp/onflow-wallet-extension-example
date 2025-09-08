# No-Build FCL Harness

This is a standalone, no-build version of the FCL harness designed for e2e testing. It provides the same functionality as the original React-based harness but without requiring any build tools or external dependencies.

## Features

- **Flow Network Integration**: All original FCL commands (Login, Logout, Queries, Mutations)
- **EVM Network Integration**: Wallet connection support with mock fallback
- **Same API**: Maintains identical function signatures and event handling as the original harness
- **No Dependencies**: Self-contained HTML file with embedded JavaScript
- **E2E Testing Ready**: Perfect for automated testing scenarios

## Usage

1. Open `index-no-build.html` in any modern web browser
2. No build step or server required - works directly from the file system
3. All functionality is available immediately

## Available Commands

### Flow Commands
- **Log In**: Initiates Flow wallet authentication
- **Log Out**: Disconnects from Flow wallet
- **Query 1 (no args)**: Executes a simple Cadence query returning `7`
- **Query 2 (args)**: Executes a Cadence query with arguments `5 + 7 = 12`
- **Mutate 1 (no args)**: Executes a simple transaction
- **Mutate 2 (args)**: Executes a transaction with arguments

### EVM Commands
- **Connect/Disconnect Wallet**: Manages EVM wallet connections
- Supports MetaMask and other Web3 wallets
- Falls back to mock connection for testing environments

## Global API

The harness exposes the same global objects as the original:

```javascript
window.fcl          // Flow Client Library mock
window.t            // Flow types
window.flowCommands // Flow command functions
window.evmCommands  // EVM command functions
```

## Event Handling

The harness maintains the same event listeners:

- `FLOW::TX` events for transaction updates
- `message` events for cross-frame communication
- Transaction status subscriptions (PENDING → FINALIZED → SEALED)

## Mock Implementation

For e2e testing purposes, this version includes mock implementations that:

- Simulate realistic Flow authentication flows
- Generate mock transaction IDs and status updates
- Provide predictable query responses
- Support both real and mock EVM wallet connections

## Differences from Original

- Uses mock implementations instead of real FCL/wagmi libraries
- Self-contained with no external CDN dependencies
- Simplified UI styling (functionality over appearance)
- Immediate availability without build process

## Perfect for E2E Tests

This harness is specifically designed for automated testing scenarios where:

- No build step is desired
- Predictable, fast responses are needed
- External network dependencies should be minimized
- Real wallet interactions can be simulated