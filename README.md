# VaultForge - Advanced Bitcoin-Backed Lending Protocol

## Overview

VaultForge is a sophisticated decentralized finance (DeFi) lending protocol built on Stacks that leverages Bitcoin's security through innovative Layer 2 architecture. The protocol enables users to deposit STX tokens as collateral and borrow against them while maintaining the trustless, permissionless principles of Bitcoin.

## Key Features

- **Bitcoin-Inherited Security**: Utilizes Stacks' Layer 2 architecture to inherit Bitcoin's robust security guarantees
- **Over-Collateralized Lending**: Implements safe lending through mandatory over-collateralization
- **Dynamic Risk Management**: Real-time position tracking with automated liquidation mechanisms
- **Transparent Operations**: All protocol parameters and operations are fully auditable on-chain
- **Fail-Safe Design**: Comprehensive error handling and overflow protection

## System Architecture

### Core Components

```
┌─────────────────────────────────────────────────────────────┐
│                    VaultForge Protocol                       │
├─────────────────────────────────────────────────────────────┤
│  ┌─────────────────┐  ┌─────────────────┐  ┌──────────────┐ │
│  │   Collateral    │  │    Borrowing    │  │ Liquidation  │ │
│  │   Management    │  │    Engine       │  │   Engine     │ │
│  └─────────────────┘  └─────────────────┘  └──────────────┘ │
│  ┌─────────────────┐  ┌─────────────────┐  ┌──────────────┐ │
│  │   Position      │  │      Risk       │  │ Governance   │ │
│  │   Tracking      │  │   Assessment    │  │   Controls   │ │
│  └─────────────────┘  └─────────────────┘  └──────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

### Contract Architecture

#### Data Structures

**User Positions**

- `total-collateral`: Total STX deposited as collateral
- `total-borrowed`: Total STX borrowed against collateral
- `loan-count`: Number of active loans

**Loans** (Future implementation)

- Individual loan tracking with interest calculations
- Temporal data for compound interest computation
- Borrower identification and loan status

#### Protocol Parameters

| Parameter | Default Value | Description |
|-----------|---------------|-------------|
| Minimum Collateral Ratio | 150% | Required over-collateralization |
| Liquidation Threshold | 130% | Automatic liquidation trigger |
| Protocol Fee | 1% | Platform fee on operations |
| Max Collateral Ratio | 500% | Upper bound for collateral ratio |
| Min Collateral Ratio | 110% | Lower bound for collateral ratio |

## Data Flow

### Deposit Flow

```
User → [Deposit STX] → Contract Validation → Update Position → Increase Total Deposits
```

### Borrow Flow

```
User → [Request Borrow] → Collateral Check → Risk Assessment → Transfer STX → Update Position
```

### Repayment Flow

```
User → [Repay STX] → Balance Verification → Update Position → Decrease Total Borrows
```

### Liquidation Flow

```
Liquidator → [Identify Under-collateralized Position] → Ratio Check → Liquidate → Update Protocol Stats
```

## Core Functions

### User Operations

#### `deposit()`

Deposits the user's entire STX balance as collateral into the protocol.

#### `borrow(amount)`

Borrows STX against deposited collateral with automatic collateral ratio validation.

#### `repay(amount)`

Repays borrowed STX, reducing the user's debt position.

#### `withdraw(amount)`

Withdraws collateral while maintaining minimum collateral requirements.

### Protocol Operations

#### `liquidate(user)`

Liquidates under-collateralized positions to protect protocol solvency.

### Administrative Functions

#### `set-minimum-collateral-ratio(new-ratio)`

Updates the minimum collateral ratio (owner only).

#### `set-liquidation-threshold(new-threshold)`

Updates the liquidation threshold (owner only).

#### `set-protocol-fee(new-fee)`

Updates the protocol fee (owner only).

## Security Features

### Multi-Layer Validation

- Input parameter validation
- Collateral ratio enforcement
- Balance verification
- Authorization checks

### Economic Security

- Over-collateralization requirements
- Automated liquidation mechanisms
- Protocol fee caps
- Emergency parameter bounds

### Technical Security

- Overflow protection
- Comprehensive error handling
- Atomic operations
- Fail-safe mechanisms

## Risk Management

### Collateral Requirements

- **Minimum Ratio**: 150% collateralization required
- **Liquidation Trigger**: 130% ratio triggers automatic liquidation
- **Safety Buffer**: 20% buffer between minimum and liquidation thresholds

### Liquidation Mechanics

- Public liquidation function for protocol health
- Instant liquidation upon threshold breach
- Complete position closure to prevent partial liquidations

## Getting Started

### Prerequisites

- Stacks wallet with STX tokens
- Understanding of DeFi lending mechanics
- Familiarity with over-collateralized lending

### Basic Usage

1. **Deposit Collateral**: Call `deposit()` to stake STX tokens
2. **Borrow STX**: Use `borrow(amount)` to access liquidity
3. **Manage Position**: Monitor collateral ratio to avoid liquidation
4. **Repay Debt**: Use `repay(amount)` to reduce borrowed amount
5. **Withdraw Collateral**: Call `withdraw(amount)` to retrieve excess collateral

## Protocol Metrics

The protocol provides real-time metrics through `get-protocol-stats()`:

- Total deposits across all users
- Total borrowed amount
- Current protocol parameters
- System health indicators

## Risk Warnings

⚠️ **Important Risk Considerations**:

- Liquidation risk if collateral ratio falls below threshold
- Market volatility can affect collateral values
- Smart contract risk inherent in DeFi protocols
- Protocol parameter changes by governance

## Technical Specifications

- **Blockchain**: Stacks (Bitcoin Layer 2)
- **Language**: Clarity Smart Contract Language
- **Security Model**: Bitcoin-inherited proof-of-work
- **Consensus**: Proof-of-Transfer (PoX)

## Future Enhancements

- Dynamic interest rate models
- Multi-collateral support
- Governance token implementation
- Advanced liquidation mechanisms
- Integration with other DeFi protocols

## Support

For technical support, protocol questions, or governance discussions, please refer to the official VaultForge documentation and community channels.

---

## VaultForge Protocol - Securing DeFi with Bitcoin's strength
