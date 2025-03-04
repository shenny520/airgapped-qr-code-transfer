## 使用方法：

1. 使用有摄像头的设备打开 scanner.html, 或者使用 OBS 等虚拟摄像头软件, 确认赋予摄像头权限，点击【Starter Receiver】开始接收
2. 在发送端打开 generator.html，选择要发送的文件，点击【Start Transfer】开始发送
3. 检查 chunks 是否完整，如果缺失，点击 scanner.html 的【Copy Missed Chunks】将缺失的 chunks 复制到剪切板, 粘贴 chunks 到 generator.html 的 Chunks 输入框，点击【Start Transfer】继续发送

****

forked from: https://github.com/mohankumarelec/airgapped-qr-code-transfer
## 原始文档

# Airgapped QR Code Transfer Web App

Airgapped QR Code Transfer is a simple web-based tool to transfer data between devices using QR codes. It allows for the transfer of files without the need for network connectivity, leveraging QR codes to encode and decode file data. This project uses Vue.js for the frontend and libraries like pako for compression, qrcode.js for QR code generation, and zbar-wasm for QR code scanning.

[![Open in Flexpilot AI Web IDE](https://badges.flexpilot.ai/open-in-web-ide.svg)](https://flexpilot.ai/web-ide-redirect?provider=github&owner=mohankumarelec&repo=airgapped-qr-code-transfer&branch=master)

## Live Online Demo

1. **Receiver Setup:**
   - Open <a href="scanner.html" target="_blank">scanner.html</a> in the receiver's browser.
   - Allow access to the camera for scanning.

2. **Sender Setup:**
   - Open <a href="generator.html" target="_blank">generator.html</a> in the sender's browser.
   - Upload the file that needs to be transferred.

3. **Transfer Process:**
   - Click the "Start Receiver" button in the receiver's browser and point it to the sender's screen.
   - In the sender's browser, click "Choose file" and then click "Start Transfer."
   - Wait for all parts to be transferred. The file will be downloaded on the receiver's device.

## Features

- **Data Sender Mode**: Allows a user to select a file, compress it, and transfer it via QR codes.
- **Data Receiver Mode**: Allows a user to scan QR codes to receive and reconstruct the file.
- **File Compression**: Uses gzip compression to reduce the size of the data being transferred.
- **QR Code Generation and Scanning**: Uses qrcode.js for generation and zbar-wasm for scanning QR codes.

## Getting Started

### Prerequisites

- A modern web browser (preferably Chrome or Firefox) that supports JavaScript and the WebRTC API.

### Installing

1. Clone the repository:

```sh
git clone https://github.com/mohankumarelec/airgap-qr-transfer.git
cd airgap-qr-transfer
```

2. Open the `generator.html` file in your browser for the sender interface:

```sh
open generator.html
```

3. Open the `scanner.html` file in your browser for the receiver interface:

```sh
open scanner.html
```

## Usage

### Data Sender Mode

1. Open `generator.html` in your browser.
2. Select a file using the file input.
3. Click the "Start Transfer" button to begin the transfer process.
4. The application will compress the file, split it into chunks, and generate QR codes for each chunk.
5. The generated QR codes will be displayed one by one, which can be scanned by the receiving device.

### Data Receiver Mode

1. Open `scanner.html` in your browser.
2. Click the "Start Receiver" button to begin the receiving process.
3. Use the device's camera to scan the QR codes generated by the sender.
4. The application will decode the QR codes, reconstruct the file, and prompt you to download it once the transfer is complete.

## How It Works

### Data Sender (generator.html)

1. **File Selection**: User selects a file from their device.
2. **Compression**: The file is compressed using the pako library.
3. **Chunking**: The compressed file is split into smaller chunks.
4. **QR Code Generation**: Each chunk is encoded into a QR code using qrcode.js.
5. **Display QR Codes**: The QR codes are displayed sequentially for the receiver to scan.

### Data Receiver (scanner.html)

1. **QR Code Scanning**: The device's camera scans QR codes using zbar-wasm.
2. **Decoding**: Each QR code is decoded to extract the chunk of data.
3. **Reconstruction**: The chunks are reassembled into the original compressed file.
4. **Decompression**: The file is decompressed using pako.
5. **File Download**: The reconstructed file is made available for download.

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes.
4. Commit your changes (`git commit -am 'Add new feature'`).
5. Push to the branch (`git push origin feature-branch`).
6. Create a new Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [Vue.js](https://vuejs.org/) - JavaScript framework for building user interfaces.
- [pako](https://github.com/nodeca/pako) - Compression library.
- [qrcode.js](https://github.com/davidshimjs/qrcodejs) - QR code generation library.
- [zbar-wasm](https://github.com/undecaf/zbar-wasm) - QR code scanning library.
