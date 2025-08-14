# Turbine Protocol

A decentralized liquidity engine built on Stacks, powering efficient token swaps with mechanical precision.

## Overview

Turbine is an automated market maker (AMM) protocol that uses an innovative "engine" metaphor to manage liquidity pools. The protocol maintains dual fuel tanks (STX and secondary tokens) and generates power units representing liquidity provider shares. With built-in mechanical friction (0.3% fee), Turbine ensures sustainable operations while providing optimal trading efficiency.

## Key Features

### 🔋 Dual Fuel System
- **Primary Fuel Tank**: STX reserves
- **Secondary Fuel Tank**: Partner token reserves
- **Dynamic Balance**: Automatic rebalancing through trading operations

### ⚡ Power Unit Distribution
- Liquidity providers receive power units proportional to their contribution
- Power units represent ownership stakes in the liquidity pool
- Redeemable for proportional shares of both fuel types

### 🔧 Engine Operations
- **Start Engine**: Initialize liquidity pool with dual token deposits
- **Refuel**: Add liquidity to increase pool depth and earn power units
- **Drain**: Remove liquidity by burning power units
- **Convert**: Execute token swaps with automated pricing

### 📊 Performance Monitoring
- Real-time fuel level tracking
- Power unit holdings per participant
- Operation history and analytics
- Engine status monitoring

## Smart Contract Functions

### Engine Management
```clarity
(start-engine fuel-interface primary-fuel secondary-fuel)
(refuel-engine fuel-interface primary-fuel secondary-fuel min-power-units)
(drain-engine fuel-interface power-units min-primary min-secondary)
```

### Trading Operations
```clarity
(execute-primary-to-secondary-conversion fuel-interface input min-output)
(execute-secondary-to-primary-conversion fuel-interface input min-output)
```

### Monitoring Functions
```clarity
(monitor-fuel-levels)
(monitor-power-units holder)
(monitor-engine-status)
(calculate-fuel-output input input-tank output-tank)
```

## How It Works

### 1. Engine Initialization
The protocol begins when the first liquidity provider "starts the engine" by depositing equal values of STX and a secondary token. This creates the initial fuel reserves and mints power units.

### 2. Liquidity Provision
Additional providers can "refuel" the engine by adding proportional amounts of both tokens, receiving power units that represent their ownership stake in the pool.

### 3. Token Swaps
Traders can convert between fuel types using the automated pricing algorithm, which maintains pool balance while extracting a small mechanical friction fee.

### 4. Liquidity Removal
Power unit holders can "drain" fuel from the engine, burning their units to receive proportional amounts of both token types.

## Technical Specifications

- **Fee Structure**: 0.3% mechanical friction on all conversions
- **Pricing Model**: Constant product formula with efficiency adjustments
- **Slippage Protection**: Minimum output requirements on all operations
- **Access Control**: Engine controller permissions for administrative functions

## Getting Started

### For Liquidity Providers
1. Start the engine or refuel an existing pool
2. Receive power units representing your stake
3. Earn fees from trading activity
4. Drain fuel when ready to exit

### For Traders
1. Check fuel levels and calculate expected outputs
2. Execute conversions with appropriate slippage tolerance
3. Monitor operation logs for transaction history

## Security Features

- **Authorization Checks**: All operations verify caller permissions
- **Parameter Validation**: Input sanitization prevents invalid operations
- **Slippage Protection**: Minimum output requirements protect against sandwich attacks
- **Engine State Management**: Status checks ensure operations occur in valid states

## Error Handling

The protocol includes comprehensive error handling:
- `engine-err-unauthorized-access`: Permission denied
- `engine-err-liquidity-exhausted`: Insufficient reserves
- `engine-err-parameter-invalid`: Invalid input parameters
- `engine-err-execution-bounds`: Slippage protection triggered
- `engine-err-fuel-type-mismatch`: Wrong token interface
- `engine-err-mechanical-failure`: Internal operation failure

## Contract Architecture

### Data Storage
- **Fuel Tanks**: Primary (STX) and secondary token reserves
- **Power Units**: Total supply and individual holdings
- **Operation Logs**: Historical transaction records
- **Engine Status**: Active/inactive state management

### Trait Compliance
Turbine requires secondary tokens to implement the `engine-fuel` trait, ensuring compatibility with standard token operations including transfers, balance queries, and metadata access.

## License

This project is open source and available under standard blockchain development licenses.

## Contributing

Contributions to the Turbine Protocol are welcome. Please ensure all code changes include appropriate tests and documentation updates.
