# Celestia Bridge Health Checker (Web)

A simple and effective tool to check the health of your Celestia Bridge node.

## About

This service allows Celestia node operators to verify if their bridge node is online, responsive, and properly configured for RPC access.

## Usage

You can use the checker directly via our hosted web interface.

1. Open the RPC port on your node:
   - Mainnet:
     ```bash
     sed -i '/$begin:math:display$RPC$end:math:display$/,/^\[/ s/Address = "localhost"/Address = "0.0.0.0"/' $HOME/.celestia-bridge/config.toml
     sudo systemctl restart celestia-bridge
     ```
   - Testnet:
     ```bash
     sed -i '/\[RPC\]/,/^\[/ s/Address = "localhost"/Address = "0.0.0.0"/' $HOME/.celestia-bridge-mocha-4/config.toml
     sudo systemctl restart celestia-bridge
     ```

2. Gather required data:
   - Get your IP:
     ```bash
     hostname -I
     ```
   - Get your port:
     ```bash
     awk -F' = ' '/\[RPC\]/ {flag=1; next} flag && /Port/ {gsub(/"/, "", $2); print $2; exit}'
     ```
   - Get your authentication token:
     ```bash
     celestia bridge auth read
     ```

3. Visit the website and input the data to check your node.

## Examples

### 1. Homepage of the Celestia Bridge Health Checker



### 2. Filled-in form ready for check



### 3. Successful check result



## Links

- [Live Checker (Web)](https://dteam.tech/tools/celestia-bridge-health-checker)
- [Celestia Docs](https://docs.celestia.org/)

## Powered by

This tool is developed and maintained by [DTEAM](https://dteam.tech), supporting decentralized infrastructure.
