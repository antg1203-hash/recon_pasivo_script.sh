# 🔍 Passive Recon Script

> **Automated passive reconnaissance tool** to identify public information about domains without direct contact. Extracts historical URLs, sensitive endpoints and more.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Bash](https://img.shields.io/badge/Shell_Script-%23121011?logo=gnu-bash&logoColor=white)](https://www.gnu.org/software/bash/)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)

---

## 📋 Table of Contents

- [What does it do?](#what-does-it-do)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Examples](#examples)
- [Output Structure](#output-structure)
- [Features](#features)
- [Troubleshooting](#troubleshooting)
- [License](#license)

---

## 🎯 What does it do?

This script automates passive reconnaissance of a domain:

✅ **Extracts `robots.txt`** - Discovers which paths the site tries to hide from search engines  
✅ **Searches historical URLs** - Retrieves snapshots from Wayback Machine  
✅ **Filters sensitive endpoints** - Identifies suspicious paths (api, admin, backup, etc.)  
✅ **Generates detailed logs** - Complete execution summary  
✅ **Robust error handling** - Domain and tool validation  

---

## 📦 Requirements

### System Tools
- `bash` (4.0+)
- `curl` 
- `grep`
- `sort`
- `awk`
- `wc`

### External Tools

| Tool | Installation |
|------|--------------|
| **waybackurls** | `go install github.com/tomnomnom/waybackurls@latest` |

> 💡 **Make sure `$GOPATH/bin` is in your `$PATH`**

---

## 🚀 Installation

### 1️⃣ Clone the repository

```bash
git clone https://github.com/antg1203-hash/recon_pasivo_script.sh.git
cd recon_pasivo_script.sh
```

### 2️⃣ Install dependencies

```bash
# On Ubuntu/Debian
sudo apt-get install curl grep

# Install waybackurls
go install github.com/tomnomnom/waybackurls@latest
```

### 3️⃣ Make the script executable

```bash
chmod +x script
```

### 4️⃣ (Optional) Add to PATH

```bash
sudo ln -s $(pwd)/script /usr/local/bin/passive_recon
# Now you can run: passive_recon example.com
```

---

## 💻 Usage

### Basic Syntax

```bash
./script <domain>
```

### Examples

```bash
# Simple reconnaissance
./script example.com

# With subdomain
./script sub.example.com

# View logs in real-time
./script google.com && cat recon_google.com/recon.log
```

---

## 📊 Output Structure

The script creates a `recon_<domain>/` folder with:

```
recon_example.com/
├── recon.log           # Detailed execution log
├── robots.txt          # Site's robots.txt file
├── wayback.txt         # Historical URLs found
└── endpoints.txt       # Filtered sensitive endpoints
```

### Example Output

```
[*] Starting reconnaissance for example.com...
[*] Extracting robots.txt...
✓ robots.txt downloaded
[*] Searching for historical URLs...
✓ 142 URLs found in Wayback Machine
[*] Filtering sensitive endpoints...
✓ 4 sensitive endpoints found

[+] ✅ Reconnaissance completed in recon_example.com
[+] Generated files:
    robots.txt (1.2K)
    wayback.txt (8.4K)
    endpoints.txt (310B)
    recon.log (2.1K)
```

---

## ✨ Features

### 🔒 Security
- ✅ Domain validation with regex
- ✅ Undefined variable detection (`set -u`)
- ✅ Error handling in pipes (`set -o pipefail`)
- ✅ Command injection prevention

### 📝 Logging
- ✅ Persistent log file
- ✅ Screen + file output simultaneously
- ✅ Result counters
- ✅ File size information

### 🛡️ Robustness
- ✅ Tool verification before execution
- ✅ Graceful failure handling
- ✅ File validation before processing

---

## 🔧 Troubleshooting

### ❌ Error: "waybackurls: command not found"

```bash
# Make sure Go is installed
go version

# Install waybackurls
go install github.com/tomnomnom/waybackurls@latest

# Verify it's in PATH
which waybackurls

# If not found, add to .bashrc or .zshrc
export PATH="$PATH:$(go env GOPATH)/bin"
source ~/.bashrc
```

### ❌ Error: "Invalid domain"

The domain contains invalid characters. Use only:
- Letters: `a-z`, `A-Z`
- Numbers: `0-9`
- Dots: `.`
- Hyphens: `-`

```bash
# ❌ Wrong
./script example.com/path

# ✅ Correct
./script example.com
```

### ⚠️ No results from Wayback Machine

Some new or private domains have no snapshots. Verify:
```bash
# Manually in your browser
https://web.archive.org/web/*/example.com
```

### 📝 View the logs

```bash
# Full log
cat recon_example.com/recon.log

# Last lines
tail -f recon_example.com/recon.log
```

---

## ⚖️ Legal Disclaimer

**⚠️ IMPORTANT**

This script is for:
- ✅ Education and learning
- ✅ Authorized testing on your own domains
- ✅ Security audits with permission

**Prohibited:**
- ❌ Use against domains without authorization
- ❌ Unauthorized data collection
- ❌ Unauthorized access to systems

The author is not responsible for malicious use.

---

## 📄 License

This project is licensed under the **MIT License**.

See [LICENSE](LICENSE) for details.

---

## 👤 Author

**antg1203-hash**

- GitHub: [@antg1203-hash](https://github.com/antg1203-hash)
- Repository: [recon_pasivo_script.sh](https://github.com/antg1203-hash/recon_pasivo_script.sh)

---

## 🤝 Contributing

Pull requests are welcome! For major changes:

1. Fork the repo
2. Create a branch (`git checkout -b feature/improvement`)
3. Commit your changes (`git commit -am 'Add improvement'`)
4. Push to the branch (`git push origin feature/improvement`)
5. Open a Pull Request

---

## 📞 Support

Having issues? Open an [issue](https://github.com/antg1203-hash/recon_pasivo_script.sh/issues)

---

<div align="center">

**⭐ If you found this useful, give it a star!**

</div>
