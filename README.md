# Passive Recon Script

A simple Bash script to perform **passive reconnaissance** on a domain.

## What it does

- Extracts `robots.txt`
- Retrieves historical URLs from Wayback Machine
- Filters sensitive endpoints (api, admin, backup, etc.)
- Generates a log file with a summary

## Requirements

- `curl`
- `grep`
- `sort`
- `awk`
- `waybackurls` (https://github.com/tomnomnom/waybackurls)

## Installation

Clone the repository:

```bash
git clone https://github.com/tu-usuario/tu-repo.git
cd tu-repo
## Make the script executable:
chmod +x recon_pasivo.sh
## usage:
./recon_pasivo.sh example.com
The output will be saved in a folder called recon_example.com/.
## Example output
[*] Iniciando reconocimiento de example.com...
[*] Extrayendo robots.txt...
✓ robots.txt descargado
[*] Buscando URLs históricas...
✓ 142 URLs encontradas en Wayback Machine
[*] Filtrando endpoints sensibles...
✓ 4 endpoints sensibles encontrados

[+] ✅ Reconocimiento completado en recon_example.com
[+] Archivos generados:
    robots.txt (1.2K)
    wayback.txt (8.4K)
    endpoints.txt (310B)
## Legal Disclaimer
This tool is for educational and authorized testing purposes only.
Do not use it against domains you do not own or have permission to test.
## License
This project is licensed under the MIT License - see the LICENSE file for details.
