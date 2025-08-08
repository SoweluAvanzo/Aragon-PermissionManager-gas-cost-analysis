# 🔬 Aragon Permission Manager – Gas Cost Analysis

This repository is a **research fork** of the Aragon OSx protocol contracts, created with the sole purpose of simulating and analyzing the **gas consumption** of the DAO **PermissionManager** contract under various scenarios.

> ⚠️ **This repository is not intended for production or deployment.**  
> It is meant solely to **replicate and validate** our gas cost measurements and generate the `gas-report.csv` file used in our analysis.

---

## 📌 Scope of this Repository

This repo focuses on:

- Simulating the execution of the `PermissionManager` contract under different conditions:
  - Granting and revoking **1**, **3**, and **6 permissions**
  - Using both **individual** and **bulk** permission operations
  - Deploying the contract and checking permission behavior in DAO action executions

- Logging **gas consumption** via Hardhat during:
  - `grant`, `revoke`, and `applyMultiTargetPermissions` calls
  - `dao.execute` operations involving permissioned actions

- Exporting results to a **CSV file**, then **post-processing** them in a Jupyter notebook to compute metrics like **average gas usage per operation**.

---

## ⚙️ Technical Details

- This project uses the **Hardhat optimizer with 200 runs** (enabled in `hardhat.config.ts`)
- Gas logs are written into `gas-report.csv`
- Results are analyzed via the provided notebook `gas-report-analysis.ipynb`

---

## 📝 Modifications from Aragon OSx

We based our work on the official Aragon OSx repo and have **only modified two test files** to enable gas metering:

| File | Changes Made |
|------|---------------|
| `test/core/dao/dao.ts` | Wrapped key `dao.execute` test cases with `logGasUsage()` to track gas usage |
| `test/core/permission/permissionManager.ts` | Added `logGasUsage()` to tests for `grant`, `revoke`, and `applyMultiTargetPermissions` |

**All other files remain unchanged** from the original Aragon OSx source.

---

## 📦 Installation & Usage

Clone the repository and run:

```bash
npm install
npx hardhat test
