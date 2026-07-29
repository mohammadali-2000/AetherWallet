# 📝 Handwritten Learning Notes: AetherWallet Protocol

> **Personal Study & Video Script Guide**  
> *Topic: How Satellite-Backed AI Wallets & Hardware Key Isolation Work*

---

## 💡 Concept Breakdown (Explain Like I'm 5)

### 1. What is the Problem with Normal Crypto Wallets?
- Normally, when you use MetaMask or a web wallet, your **private key is stored inside your browser**.
- If a website gets hacked or you click a phishing link, malicious code can trick your browser into signing a transaction that steals all your funds.
- If an AI Agent manages your funds, putting private keys directly inside the AI script is dangerous because a prompt injection attack can steal the key.

### 2. How AetherWallet Solves This (The 4 Security Guardrails)

```
[ Your Browser ] ---> [ AI Security Agent ] ---> [ Satellite KMS Signer ] ---> [ EVM Chain ]
 (Creates Intent)      (Analyzes Risk)           (Signs Isolated Key)        (Executes Tx)
```

1. **Intent vs. Key Separation**: The user or AI agent creates *intent* (e.g. "I want to swap 0.1 ETH for USDC"). Neither the browser nor the AI agent holds the private key.
2. **AI Risk Inspection**: The AI agent acts like a security guard. It checks:
   - Is the recipient address blacklisted?
   - Is the gas fee reasonable?
   - Is there unlimited token approval danger?
3. **Space KMS Hardware Signing**: The raw transaction hash is sent to an isolated hardware key enclave (Space Computer / KMS). The private key **never leaves the hardware**.
4. **Swarm Memory Audit Trail**: The session details and AI safety analysis are encrypted and uploaded to **Swarm** (decentralized storage). Anyone can audit what happened, but no central server can modify the history.

---

## 🎬 60-Second Video Script (For Twitter / LinkedIn)

Use this exact script when recording your 60-second Loom or screen video:

> **[0:00 - 0:15 Intro]**  
> *"What happens when an AI Agent needs to execute blockchain transactions, but you can't trust it with your private key? Meet AetherWallet — an orbital AI wallet built with 4 security trust layers."*
>
> **[0:15 - 0:35 Demo]**  
> *"Here in the local interface, I create a transaction intent — like swapping ETH for USDC. The Aether AI Agent inspects the transaction payload in real-time for phishing risk or excessive approvals. Once approved, the signature request is dispatched to an isolated Space KMS enclave. The private key never touches the browser."*
>
> **[0:35 - 0:50 Memory]**  
> *"All session audit logs are encrypted and permanently written to Swarm decentralized storage, creating a tamper-proof memory trail for AI actions."*
>
> **[0:50 - 1:00 Outro]**  
> *"Check out the live code on my GitHub link below!"*

---

## 🛠️ Code Deep-Dive: Key Files to Know

1. **`wallet/server.ts`**: The main local server handling key initialization, RPC interaction via Viem, and security policy checks.
2. **`wallet/cli.ts`**: Command-line interface for hardware enclave interaction and transaction dispatch.
3. **`agents/index.js`**: The AI security agent logic that uses OpenAI/Gemini to evaluate risk before signing.

---

*Notes created for Ali's Public Web3 Portfolio | July 2026*
