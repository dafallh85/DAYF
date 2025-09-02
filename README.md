# ✨DAYF

It is an intelligent robotics project that aims to develop and program intelligent robots that learn and interact with their surrounding environment. DAYF
# DAYF Token


---**Currency Code**: DAYF
**Currency Network**: Binance Smart Chain (BEP-20)
**Total Supply**: 1,000,000,000 DAYF

## 💡 ما هي DAYF؟

.DAYF is a smart cryptocurrency project operating on the BNB (BEP-20) network, aiming to enable secure and fast financial solutions, and easy integration into smart future applications, especially in areas related to artificial intelligence and automated systems.

---

## 🔗 روابط مهمة

# DAYF Token

**DAYF** — The world's first intelligent robotics token 🤖💎  
Empowering AI, DeFi, and Web3 in a unified ecosystem.

## Official Links

- 🌐 Website: [https://smartdayf.com](https://smartdayf.com)  
- 🐦 Twitter :  https://x.com/smartdayf
- 💬 Telegram Official
- https://t.me/SmartDAYF
- (https://t.me/SMRTDAYF)  
- 👥 Telegram Community: [https://t.me/DAYFDAYF](https://t.me/DAYFDAYF)  
- 📌 Telegram Support / Contact: [https://t.me/Token_Officer](https://t.me/Token_Officer)  
- 📧 Email: dayf@smartdayf.com

## Contract

- **Token:** DAYF  
- **Contract Address:** 0x6206Dd029512fe34e8320Df8e62d0E9B5a04659A  
- **Network:** BNB (BEP-20)  

## Features

- Intelligent AI integration 🤖  
- Automated trading & portfolio management 💹  
- Staking & rewards system 💸  
- Governance voting 🗳️  
- Community-driven development 🌐  

---
## 🔐 Smart contract code

The DAYF contract has been published on BscScan and can be reviewed in the `contracts/DAYF.sol` folder.

---https://bscscan.com/token/0x6206dd029512fe34e8320df8e62d0e9b5a04659a

## 📁 المجلدات

- `contracts/` يحتوي على الكود البرمجي للعقد الذكي.
- `assets/` مخصص للشعار والصور الخاصة بالمشروع.
- `docs/` لتوثيق المشروع.
- `scripts/` لأي سكربتات أو أدوات داعمة.

---

## 📜 العقد الذكي (ملف: contracts/DAYF.sol)

```solidity
pragma solidity ^0.8.2;

contract Token {
    mapping(address => uint) public balances;
    mapping(address => mapping(address => uint)) public allowance;
    uint public totalSupply = 1000000000 * 10 ** 18;
    string public name = "DAYF";
    string public symbol = "DAYF";
    uint public decimals = 18;
    
    event Transfer(address indexed from, address indexed to, uint value);
    event Approval(address indexed owner, address indexed spender, uint value);
    
    constructor() {
        balances[msg.sender] = totalSupply;
    }
    
    function balanceOf(address owner) public view returns(uint) {
        return balances[owner];
    }
    
    function transfer(address to, uint value) public returns(bool) {
        require(balanceOf(msg.sender) >= value, 'balance too low');
        balances[to] += value;
        balances[msg.sender] -= value;
        emit Transfer(msg.sender, to, value);
        return true;
    }
    
    function transferFrom(address from, address to, uint value) public returns(bool) {
        require(balanceOf(from) >= value, 'balance too low');
        require(allowance[from][msg.sender] >= value, 'allowance too low');
        balances[to] += value;
        balances[from] -= value;
        emit Transfer(from, to, value);
        return true;   
    }
    
    function approve(address spender, uint value) public returns (bool) {
        allowance[msg.sender][spender] = value;
        emit Approval(msg.sender, spender, value);
        return true;   
    }
}
