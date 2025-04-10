## Giới Thiệu / Introduction
Tiếng Việt
0G Lab Auto Script là một công cụ tự động hóa được phát triển bởi Crazyscholar để hỗ trợ người dùng tương tác với blockchain 0G Testnet. Chương trình này cho phép người dùng mint token (Ethereum, Bitcoin, Tether) và thực hiện các giao dịch swap tự động giữa các token này. Với tính năng hỗ trợ proxy, retry khi lỗi và đa ngôn ngữ (tiếng Việt và tiếng Anh), đây là một giải pháp mạnh mẽ cho việc thử nghiệm trên testnet.

English
0G Lab Auto Script is an automation tool developed by Crazyscholar to assist users in interacting with the 0G Testnet blockchain. This program enables users to mint tokens (Ethereum, Bitcoin, Tether) and perform automated swap transactions between these tokens. Featuring proxy support, error retry mechanisms, and multilingual support (Vietnamese and English), it provides a robust solution for testnet experimentation.

## Tính Năng / Features
Mint Token: Tự động mint các token Ethereum, Bitcoin và Tether từ các hợp đồng thông minh trên 0G Testnet.
Swap Token: Thực hiện swap giữa các token với tỷ lệ ngẫu nhiên trong khoảng cấu hình.
Hỗ Trợ Proxy: Sử dụng danh sách proxy từ file proxy.txt để tăng tính ẩn danh và tránh giới hạn tốc độ.
Cơ Chế Retry: Thử lại tối đa 3 lần khi gặp lỗi (có thể tùy chỉnh trong config.json).
Đa Ngôn Ngữ: Hỗ trợ log bằng tiếng Việt hoặc tiếng Anh, tùy chọn trong config.json.
Kiểm Tra Số Dư: Bỏ qua ví nếu không đủ gas để thực hiện giao dịch.
Mint Tokens: Automatically mint Ethereum, Bitcoin, and Tether tokens from smart contracts on the 0G Testnet.
Swap Tokens: Perform swaps between tokens with random percentages within a configurable range.
Proxy Support: Utilize a proxy list from proxy.txt for anonymity and rate limit avoidance.
Retry Mechanism: Retry up to 3 times on errors (configurable in config.json).
Multilingual: Support logging in Vietnamese or English, selectable in config.json.
Balance Check: Skip wallets if there’s insufficient gas for transactions.
## Yêu Cầu / Requirements
Tiếng Việt
Node.js: Phiên bản 16 trở lên.
File cấu hình: config.json, privatekey.txt, proxy.txt.
Thư viện: Cài đặt các thư viện cần thiết qua npm.
English
Node.js: Version 16 or higher.
Configuration Files: config.json, privatekey.txt, proxy.txt.
Dependencies: Install required libraries via npm.
## Cài Đặt / Installation
Tiếng Việt

Tải source code:
Clone repository hoặc tải file index.js về máy.
```bash
git clone <repository_url>
cd 0G_Lab
```
Cài đặt thư viện:
Chạy lệnh sau để cài các thư viện cần thiết:
```bash

npm install web3 fs colors cfonts https-proxy-agent dotenv
```
Chuẩn bị file cấu hình:
Tạo file privatekey.txt: Mỗi dòng là một private key (có hoặc không có 0x).
Tạo file proxy.txt: Mỗi dòng là một proxy (định dạng http://user:pass@host:port hoặc http://host:port).
Cấu hình config.json: Sao chép từ mẫu dưới và chỉnh sửa theo nhu cầu.
Chạy chương trình:
```bash

node index.js
```
English
Download the source code:
Clone the repository or download the index.js file.
```bash

git clone <repository_url>
cd 0G_Lab
```
Install dependencies:
Run the following command to install required libraries:
```bash

npm install web3 fs colors cfonts https-proxy-agent dotenv
```
Prepare configuration files:
Create privatekey.txt: One private key per line (with or without 0x prefix).
Create proxy.txt: One proxy per line (format: http://user:pass@host:port or http://host:port).
Configure config.json: Copy from the sample below and modify as needed.
Run the program:
```bash

node index.js
```
## Cấu Hình / Configuration
Mẫu config.json / Sample config.json
```bash
{
  "rpcUrl": "https://evmrpc-testnet.0g.ai",
  "contracts": {
    "Ethereum": "0xce830D0905e0f7A9b300401729761579c5FB6bd6",
    "Bitcoin": "0x1E0D871472973c562650E991ED8006549F8CBEfc",
    "Tether": "0x9A87C2412d500343c073E5Ae5394E3bE3874F76b"
  },
  "swapRouterAddress": "0xd86b764618c6e3c078845be3c3fce50ce9535da7",
  "gasSettings": {
    "defaultGasLimitMint": 500000,
    "defaultGasLimitApprove": 100000,
    "defaultGasLimitSwap": 300000,
    "gasPriceMultiplier": 1.2
  },
  "swapSettings": {
    "minSwapPercentage": 0.05,
    "maxSwapPercentage": 0.10,
    "slippageTolerance": 0.05
  },
  "retrySettings": {
    "maxRetries": 3,
    "retryDelay": 15000
  },
  "transactionSettings": {
    "maxTransactionCount": 100,
    "transactionTimeout": 300000,
    "retryDelay": 15000
  },
  "concurrencyLimit": 5,
  "language": "vi" // "vi" hoặc "en"
}
```
## Giải Thích / Explanation

rpcUrl: Đường dẫn RPC của 0G Testnet.
contracts: Địa chỉ hợp đồng của các token.
swapRouterAddress: Địa chỉ router để swap token.
gasSettings: Cài đặt gas cho các giao dịch.
swapSettings: Tỷ lệ swap và dung sai trượt giá.
retrySettings: Số lần thử lại và độ trễ khi lỗi.
language: Chọn "vi" (tiếng Việt) hoặc "en" (tiếng Anh).
Cách Sử Dụng / Usage
Tiếng Việt
Thêm ví: Thêm private key vào privatekey.txt.
Thêm proxy: Thêm proxy vào proxy.txt (tùy chọn).
Chỉnh ngôn ngữ: Mở config.json, đặt "language": "vi" hoặc "language": "en".
Chạy: Mở terminal và chạy node index.js.
Xem log: Kiểm tra log trong terminal để theo dõi quá trình mint và swap.
English
Add wallets: Add private keys to privatekey.txt.
Add proxies: Add proxies to proxy.txt (optional).
Set language: Open config.json, set "language": "vi" or "language": "en".
Run: Open a terminal and run node index.js.
Check logs: Monitor the terminal logs to track minting and swapping processes.

## Lưu Ý / Notes

RPC Stability: Nếu gặp lỗi invalid json response body, kiểm tra RPC trong rpcUrls của index.js và thêm RPC dự phòng nếu cần.
Gas: Đảm bảo ví có đủ 0G để trả phí gas, nếu không ví sẽ bị bỏ qua.
Proxy: Proxy không bắt buộc, nhưng khuyến khích để tránh giới hạn từ RPC.
## !! Nếu như chương trình đã chạy đến đoạn gửi tx_hash mint token nhưng lại báo lỗi thì bạn đừng lo lắng đó là do dự án họ đang nghẽn mạng . Tôi đã kiểm tra và debug kĩ có rất nhiều ví của tôi cũng gặp tình trạng như thế khoảng sau 30p -1 giờ sau thì mới load được tx_hash đó và mint thành công!

RPC Stability: If you encounter invalid json response body errors, check the rpcUrls in index.js and add backup RPCs if necessary.
Gas: Ensure wallets have sufficient 0G for gas fees, or they will be skipped.
Proxy: Proxies are optional but recommended to bypass RPC rate limits.
## !! If the program has run to the part of sending tx_hash mint token but reports an error, don't worry, it's because the project is congested. I have checked and debugged carefully, many of my wallets also have the same problem, about 30 minutes - 1 hour later, I can load that tx_hash and successfully mint!

## Đóng Góp / Contribution
Tiếng Việt
Nếu bạn muốn đóng góp, hãy fork repository này, chỉnh sửa và gửi pull request. Mọi ý kiến đều được hoan nghênh!

English
If you’d like to contribute, fork this repository, make changes, and submit a pull request. All feedback is welcome!

Liên Hệ / Contact
## 🌐 Connect with Me
- Twitter: [@Crzscholar](https://twitter.com/Crzscholarr)
- Telegram: [@Crzscholar](https://t.me/Crzscholar)
- Email: [Crazyscholar@outlook.com.vn](mailto:Crazyscholar@outlook.com.vn)

Chúc bạn sử dụng vui vẻ! / Happy using!# 0G_Lab
