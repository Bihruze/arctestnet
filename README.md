
## Arc Testnet Contract ve Deploy Rehberi

Bu rehber, Arc Testnet üzerinde basit bir akıllı sözleşmenin baştan sona nasıl deploy edileceğini adım adım gösterir.

---

### 1. MetaMask’e Arc Testnet Ağını Ekleyin

MetaMask → Ağ Ekle → Ağı Elle Ekle

Network Name: Arc Testnet  
RPC URL: https://rpc.testnet.arc.network  
Chain ID: 5042002  
Currency Symbol: USDC  
Block Explorer: https://testnet.arcscan.app

Ağ eklendikten sonra MetaMask’ta Arc Testnet’i seçin.

---

### 2. Test USDC (Gas Ücreti İçin) Alın

Arc testnet üzerinde gas ödemesi USDC ile yapılır.

Test USDC Faucet:  
https://faucet.circle.com

Cüzdanınızı bağlayın → Test USDC talep edin.

---

### 3. Remix IDE’yi Açın

https://remix.ethereum.org adresine gidin.

Sol menü → File Explorer → Yeni Dosya → `HelloArchitect.sol` oluşturun.  
Aşağıdaki kodu yapıştırın:

````solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.30;

contract HelloArchitect {
    string private greeting;

    event GreetingChanged(string newGreeting);

    constructor() {
        greeting = "Hello Architect!";
    }

    function getGreeting() external view returns (string memory) {
        return greeting;
    }

    function setGreeting(string calldata newGreeting) external {
        greeting = newGreeting;
        emit GreetingChanged(newGreeting);
    }
}
`````

---

### 4. Derleme (Compile)

Sol menü → Solidity Compiler
Compiler Version: 0.8.30
"Compile HelloArchitect.sol" butonuna basın.

---

### 5. Deploy İşlemi

Sol menü → Deploy & Run Transactions

Environment: Injected Provider (MetaMask)
MetaMask’ta Arc Testnet seçili olmalı
Contract: HelloArchitect

"Deploy" → MetaMask’ta işlemi onaylayın.

Sözleşme artık Arc Testnet’te yayınlanmış olur.

---

### 6. Sözleşmeyi ArcScan Üzerinde Görüntüleme

[https://testnet.arcscan.app](https://testnet.arcscan.app) adresine gidin.
Sözleşme adresinizi arama kutusuna yapıştırarak görüntüleyebilirsiniz.

---

### 7. Kaynak Kod Doğrulama (Verify & Publish)

[https://testnet.arcscan.app](https://testnet.arcscan.app) üzerinde sözleşme sayfasına gidin.
"Verify & Publish Contract" seçeneğine tıklayın.

Ayarlar:

Method: Single File
Compiler Version: 0.8.30
Optimization: Remix’te ne seçtiysen aynı olmalı

HelloArchitect.sol kodunu olduğu gibi yapıştırın → Submit.

Doğrulama tamamlandığında kontrat kodu ve ABI tarayıcıda görüntülenebilir olur.

