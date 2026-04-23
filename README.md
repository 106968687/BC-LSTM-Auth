A hybrid trust verification system combining Blockchain Smart Contracts and LSTM Behavioral Trust Model for signature authenticity detection, key escrow, and attack defense.

Project Structure
Plain Text
.
├── signature_test_dataset.csv      # Signature authenticity test dataset (ground truth labeled)
├── hybrid_dataset_50k.csv           # Hybrid training dataset (50k records)
├── Registration Smart Contract (RSC).txt   # Registration Smart Contract
├── Key Escrow Smart Contract (KESC).txt    # Key Escrow Smart Contract
├── LSTM Behavioral Trust Model Source Code.txt # LSTM Behavioral Trust Model Source Code
├── Blockchain Interaction Script.txt       # Blockchain Interaction Script
├── Attack Simulation Script.txt            # Attack Simulation Script
└── README.md                                 # Project documentation

Environment Dependencies
Basic Environment
•Python 3.8+
•Git
Python Packages
bash
pip install pandas numpy tensorflow torch scikit-learn web3
Blockchain Environment
•Ganache (local test chain, recommended)
•Truffle / Hardhat (optional, for contract compilation and deployment)
•MetaMask (wallet interaction)

Dataset Description
signature_test_dataset.csv
•Fields: dataid, data_content, signature, is_genuine (1 = genuine, 0 = forged)
•Purpose: Model testing and signature authenticity verification
hybrid_dataset_50k.csv
•Scale: 50,000 mixed transaction signature records
•Purpose: Training the LSTM Behavioral Trust Model

Experiment Reproduction Steps
Step 1: Clone the Project
bash
git clone [your repository URL]
cd [project folder]
Step 2: Dataset Preparation
1.Place signature_test_dataset.csv and hybrid_dataset_50k.csv in the root directory.
2.No preprocessing required; the code reads CSV directly.
Step 3: Deploy Blockchain Smart Contracts
1.Start Ganache local test chain (default RPC: http://127.0.0.1:7545).
2.Deploy Registration Smart Contract (RSC) via Remix / Ganache.
3.Deploy Key Escrow Smart Contract (KESC).
4.Save contract addresses and ABIs for later use.
Step 4: Run LSTM Behavioral Trust Model
1.Save model code as lstm_trust_model.py.
2.Update dataset paths:
python
train_df = pd.read_csv('hybrid_dataset_50k.csv')
test_df = pd.read_csv('signature_test_dataset.csv')
3.Run training and evaluation:
bash
python lstm_trust_model.py
4.Output: accuracy, precision, recall, signature detection results.
Step 5: Blockchain Interaction Verification
1.Save script as blockchain_interact.py.
2.Fill RPC, contract addresses, and ABIs:
python
w3 = Web3(Web3.HTTPProvider('http://127.0.0.1:7545'))
rsc_address = '[your registration contract address]'
kesc_address = '[your key escrow contract address]'
3.Run interaction:
bash
python blockchain_interact.py
Step 6: Attack Simulation Experiment
1.Save script as attack_simulation.py.
2.Run simulation:
bash
python attack_simulation.py
3.Output: attack success rate, defense effectiveness, blockchain alert records.

Expected Experimental Results
1.Signature Detection: LSTM classification accuracy ≥ 95%.
2.Blockchain Functions: Successful user registration, key escrow, signature verification.
3.Attack Defense: Forged signature & replay attack interception; alert rate ≥ 98%.

Frequently Asked Questions
1.Dataset reading failure
Check file path and file integrity.
2.Blockchain connection failure
Ensure Ganache is running; verify RPC address and port.
3.Model training error
Reduce batch_size; check TensorFlow / PyTorch version compatibility.

License
This project is for academic research only. Do not use for illegal purposes.
