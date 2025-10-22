# GOAL IN 2 WEEKS

Implement a simple but complete blockchain flow for **medicine authenticity**:

* Admin uploads medicine batch → QR + hash stored on Ethereum
* Customer scans QR → verifies authenticity from blockchain
* Optional: hash check for stock integrity

---

## 🗓️ **2-Week Practical Roadmap**

### 🔹 **WEEK 1 — Understanding & Building the Smart Contract**

**🎯 Goal:** Be able to write, deploy, and test a Solidity contract for batch authenticity.

#### Day 1–2 → *Ethereum & Blockchain Basics (only essentials)*

* What is blockchain (blocks, hashes, transactions)
* Ethereum smart contracts concept
* Gas, wallets, and MetaMask basics
* Why we store **hashes instead of full data**

🧠 Focus:

* Understand what “immutable” means
* Understand why blockchain is for verification, not live data

#### Day 3–4 → *Solidity Basics (Remix IDE)*

* Variables, Structs, and Mappings
* Functions (`public`, `view`, `onlyAdmin`)
* Events
* Writing your first contract in **Remix**

🧩 Example practice:
Create a `MedicineRegistry` contract:

```solidity
struct Batch {
  string batchId;
  string qrHash;
  bool isValid;
}
mapping(string => Batch) batches;
```

#### Day 5–6 → *Implement Real Logic*

Write your main contract with:

```solidity
function addBatch(string memory batchId, string memory qrHash) public;
function verifyBatch(string memory batchId, string memory qrHash) public view returns(bool);
```

* Emit events for `BatchCreated`
* Add `onlyAdmin` modifier

🧠 Goal by end of Week 1:
✅ Smart contract written, tested on **Remix**, and you can deploy & call it manually.

---

### 🔹 **WEEK 2 — Integration with App + QR Verification**

**🎯 Goal:** Connect the blockchain with your backend and QR system so that the full flow works end to end.

#### Day 1–2 → *Connect Blockchain with Backend*

* Learn **ethers.js** basics (simpler than web3.js)
* How to connect to your deployed contract:

  ```js
  const contract = new ethers.Contract(contractAddress, abi, signer);
  ```
* Use **Infura** or **Alchemy** to connect to Ethereum testnet (like Sepolia)
* Write simple Express routes:

  * `/addBatch` → calls `addBatch()`
  * `/verifyBatch` → calls `verifyBatch()`

🧠 Focus: Backend can call your contract.

---

#### Day 3–4 → *QR Code + Hash Integration*

* Use Node’s `crypto` module to hash QR info:

  ```js
  const hash = ethers.keccak256(ethers.toUtf8Bytes(batchId + expiry));
  ```
* Use `qrcode` npm library to generate and display QR
* When user scans → regenerate hash → compare with blockchain

🧠 Focus: Verification works end to end.

---

#### Day 5–6 → *Frontend & Testing*

* Connect MetaMask with your React admin panel
* Test the add batch + verify flow visually
* Verify that:

  * Authentic QR returns ✅ valid
  * Fake QR returns ⚠️ suspicious

🧠 Focus: Smooth working demo.

---

### ✅ **By End of Week 2 You’ll Have**

* 1 Solidity smart contract (`MedicineRegistry.sol`)
* Connected via ethers.js to your Express backend
* Admin can add batch → hash stored on blockchain
* Customer scans QR → authenticity verified via blockchain
* Optional: add hash update for stock verification

---

## 📚 Quick Reference Topics to Cover

| Category          | Topics (Exact Keywords to Study)                        |
| ----------------- | ------------------------------------------------------- |
| Blockchain Basics | Block, Transaction, Hash, Ethereum, EVM                 |
| Solidity          | Structs, Mapping, Events, Modifiers, require(), emit    |
| Tools             | Remix IDE, MetaMask, Hardhat (optional), Infura/Alchemy |
| Integration       | ethers.js basics, connectContract(), call methods       |
| Node.js           | crypto hashing, qrcode generation                       |
| Testing           | MetaMask + Remix interaction, testnet deployment        |

---

## ⚙️ **Tech Stack Summary**

| Layer                | Tool / Library                 |
| -------------------- | ------------------------------ |
| Smart Contract       | Solidity (on Ethereum testnet) |
| Wallet               | MetaMask                       |
| Blockchain Access    | Infura / Alchemy               |
| Backend              | Express.js + ethers.js         |
| Frontend             | React                          |
| Database (off-chain) | MongoDB                        |
| QR & Hashing         | qrcode, crypto (Node.js)       |

