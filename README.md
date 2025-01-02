# Void Development Setup

Welcome to Void! This guide explains how to set up Void for development, including installing dependencies, compiling, and running the app. It also includes detailed troubleshooting steps and requirements like Visual Studio tools.

---

## Prerequisites

1. **Node.js**:
   - Recommended version: **v20**.
   - Install via [Node.js Official Website](https://nodejs.org/) or `nvm`:
     ```bash
     nvm install 20
     nvm use 20
     ```

2. **Git**:
   - Ensure Git is installed and configured:
     ```bash
     git --version
     ```

3. **Python**:
   - Required for some build tools.
   - Install Python 3.x and ensure it’s in your `PATH`.

4. **Visual Studio 2022**:
   - Install the **Community Edition** from [Visual Studio](https://visualstudio.microsoft.com/).
   - During installation, select the following workloads and components:
     - **Desktop Development with C++**
     - **C++ Build Tools**
     - **MSVC v143 - VS 2022 C++ x64/x86 Build Tools**
     - **Windows 10 SDK**
     - **Spectre-mitigated Libraries**
   - Ensure `cl.exe` and related tools are accessible in your terminal.

5. **VSCode Locally Cloned**:
   - Clone the Void repository:
     ```bash
     git clone https://github.com/voideditor/void.git
     cd void
     ```

6. **Forking** (Optional):
   - Fork the repository on GitHub and update the remote:
     ```bash
     git remote add myfork https://github.com/<your-username>/void.git
     ```

---

## Setting Up Void

### 1. Install Dependencies
Run the following to install all dependencies:
```bash
npm install
```

---

### 2. Compilation

#### Compile the Project
```bash
npm run compile
```

#### Update Grammar and Localization Files
If you encounter errors, ensure all localization and grammar files are updated:
```bash
npm run update-grammars
npm run update-localization-extension -- en
```

#### Visual Studio Tools
Make sure Visual Studio is correctly configured with the required tools. If you encounter build errors, recheck your installation and ensure:
- `msbuild` is available in your terminal.
- The correct workloads and SDKs are installed.

---

### 3. Running Void

#### Using `.bat` Files
Void can be launched using the provided `.bat` file:
```bash
.\scripts\code.bat
```

#### Directly via Electron
Alternatively, you can run Void with Electron:
```bash
electron ./out/main.js
```

> **Note:** Running with Electron directly may result in missing environment variables. The `.bat` file ensures proper setup.

---

## Common Issues

### Missing `nls.messages.json`
If the app shows an empty screen, it may be due to a missing localization file:
1. Ensure the file exists:
   ```
   D:\void\out\nls.messages.json
   ```
2. If missing, create a placeholder file:
   ```json
   {}
   ```

### GitHub API Rate Limits
If you encounter rate limits while updating grammars:
1. Generate a **GitHub Personal Access Token**.
2. Set the `GITHUB_TOKEN` environment variable:
   ```bash
   export GITHUB_TOKEN=your-token-here
   ```

### Visual Studio Errors
If builds fail, ensure:
- The **Desktop Development with C++** workload is installed.
- **MSVC v143** and **Windows 10 SDK** are installed.

---

## Contributing

1. Commit your changes:
   ```bash
   git add .
   git commit -m "Your message"
   ```

2. Push changes to your fork:
   ```bash
   git push myfork main
   ```

3. Open a Pull Request to the original repository.

---

## Keeping Your Fork Updated

1. Fetch updates from the original repository:
   ```bash
   git fetch origin
   ```

2. Merge changes:
   ```bash
   git merge origin/main
   ```

3. Push to your fork:
   ```bash
   git push myfork main
   ```

---

## License

Void is licensed under the **MIT License**. See `LICENSE.txt` for details.

---

Happy coding! 💻✨
