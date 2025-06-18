# Celestia Bridge Health Checker (Web)

![bridge_health_checker_web](https://github.com/user-attachments/assets/a0aea1e9-d92f-4b6d-9b4d-29bcfa316b4a)

A simple and effective tool to check the health of your Celestia Bridge node.

---

## About

This service allows Celestia node operators to verify if their bridge node is online, responsive, and properly configured for RPC access.

## Usage

You can use the checker directly via our hosted web interface https://celestia-bridge-checker.dteam.tech.

1. Open the RPC port on your node (change the UFW settings, if applicable):
   - Mainnet:
     ```bash
     sudo sed -i '/\[RPC\]/,/^\[/ s/Address = "localhost"/Address = "0.0.0.0"/' $HOME/.celestia-bridge/config.toml
     sudo systemctl restart celestia-bridge
     ```
   - Testnet:
     ```bash
     sudo sed -i '/\[RPC\]/,/^\[/ s/Address = "localhost"/Address = "0.0.0.0"/' $HOME/.celestia-bridge-mocha-4/config.toml
     sudo systemctl restart celestia-bridge
     ```

2. Gather required data:
   - Get your IP:
     ```bash
     hostname -I
     ```
   - Get your port:
     ```bash
     #mainnet
     sudo awk -F' = ' '/\[RPC\]/ {flag=1; next} flag && /Port/ {gsub(/"/, "", $2); print $2; exit}' $HOME/.celestia-bridge/config.toml

     #testnet
     sudo awk -F' = ' '/\[RPC\]/ {flag=1; next} flag && /Port/ {gsub(/"/, "", $2); print $2; exit}' $HOME/.celestia-bridge-mocha-4/config.toml
     ```
   - Get your authentication token:
     ```bash
     #mainnet
     celestia bridge auth read

     #testnet
     celestia bridge auth read --p2p.network mocha-4
     ```

3. Visit the website and input the data to check your node.

## Examples

### 1. Homepage of the Celestia Bridge Health Checker
<img width="1500" alt="image" src="https://github.com/user-attachments/assets/85a6d989-8ef0-470a-a796-903622596551" />

### 2. Filled-in form ready for check
<img width="597" alt="image" src="https://github.com/user-attachments/assets/0259fa25-9da2-4305-b7fb-282905004f58" />

### 3. Successful check result
<img width="1203" alt="image" src="https://github.com/user-attachments/assets/c359adf5-4e2f-4b40-89fe-2388938a1dff" />

## Links

- [Live Checker (Web)](https://dteam.tech/tools/celestia-bridge-health-checker)
- [Celestia Docs](https://docs.celestia.org/)

## Contributing

We welcome all contributions to Celestia Bridge Health Checker (Web)! If you have ideas for new features, improvements, or bug fixes, feel free to open a pull request. We encourage open collaboration and appreciate your help in making this tool even more robust and user-friendly.

If you prefer to discuss or propose improvements privately, or if you need further assistance, please send us an email at **contact@dteam.tech**. We’re excited to collaborate with the community to continually enhance this service.
