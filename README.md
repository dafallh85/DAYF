# DAYF

هو مشروع روبوتات ذكي يهدف إلى تطوير وبرمجه روبوتات ذكية تتعلم وتتفاعل مع بيئتها المحيطة.  DAYF 
# DAYF Token

**رمز العملة**: DAYF  
**شبكة العملة**: Binance Smart Chain (BEP-20)  
**إجمالي المعروض**: 1,000,000,000 DAYF

---

## 💡 ما هي DAYF؟

DAYF هو مشروع عملة رقمية ذكية تعمل على شبكة BNB (BEP-20)، تهدف إلى تمكين حلول مالية آمنة وسريعة، وتكامل سهل في تطبيقات المستقبل الذكي، خصوصًا في المجالات المتعلقة بالذكاء الاصطناعي والأنظمة المؤتمتة.

---

## 🔗 روابط مهمة

- 🌐 الموقع الرسمي: [https://smartdayf.com](https://smartdayf.com)
- 🐦 تويتر (X): [https://x.com/smartdayf](https://x.com/smartdayf)
- 📧 البريد الرسمي: `dayd@smartdayf.com`
- 🧑‍💼 المؤسس على تيليجرام: `@SSMARTDAYF`
- 📣 قناة تيليجرام: [https://t.me/SmartDAYF](https://t.me/SmartDAYF)
- 👥 مناقشات المجتمع: [https://t.me/ssmartmachinesDAYF](https://t.me/ssmartmachinesDAYF)

---

## 🔐 كود العقد الذكي

تم نشر عقد عملة DAYF على BscScan ويمكن مراجعته في مجلد `contracts/DAYF.sol`.

---

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
