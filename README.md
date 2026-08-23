# 🔍 Recon Pasivo Script

> **Herramienta de reconocimiento pasivo automatizado** para identificar información pública de dominios sin contacto directo. Extrae URLs históricas, endpoints sensibles y más.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Bash](https://img.shields.io/badge/Shell_Script-%23121011?logo=gnu-bash&logoColor=white)](https://www.gnu.org/software/bash/)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)

---

## 📋 Tabla de Contenidos

- [¿Qué hace?](#qué-hace)
- [Requisitos](#requisitos)
- [Instalación](#instalación)
- [Uso](#uso)
- [Ejemplos](#ejemplos)
- [Estructura de salida](#estructura-de-salida)
- [Características](#características)
- [Solución de problemas](#solución-de-problemas)
- [Licencia](#licencia)

---

## 🎯 ¿Qué hace?

Este script automatiza el reconocimiento pasivo de un dominio:

✅ **Extrae `robots.txt`** - Descubre qué paths el sitio intenta ocultar de buscadores  
✅ **Busca URLs históricas** - Recupera snapshots de Wayback Machine  
✅ **Filtra endpoints sensibles** - Identifica paths sospechosos (api, admin, backup, etc.)  
✅ **Genera logs detallados** - Resumen completo de la ejecución  
✅ **Manejo robusto de errores** - Validación de dominios y herramientas  

---

## 📦 Requisitos

### Herramientas del sistema
- `bash` (4.0+)
- `curl` 
- `grep`
- `sort`
- `awk`
- `wc`

### Herramientas externas

| Herramienta | Instalación |
|-------------|-------------|
| **waybackurls** | `go install github.com/tomnomnom/waybackurls@latest` |

> 💡 **Asegúrate que `$GOPATH/bin` está en tu `$PATH`**

---

## 🚀 Instalación

### 1️⃣ Clonar el repositorio

```bash
git clone https://github.com/antg1203-hash/recon_pasivo_script.sh.git
cd recon_pasivo_script.sh
```

### 2️⃣ Instalar dependencias

```bash
# En Ubuntu/Debian
sudo apt-get install curl grep

# Instalar waybackurls
go install github.com/tomnomnom/waybackurls@latest
```

### 3️⃣ Dar permisos de ejecución

```bash
chmod +x recon_pasivo.sh
```

### 4️⃣ (Opcional) Agregar a PATH

```bash
sudo ln -s $(pwd)/recon_pasivo.sh /usr/local/bin/recon_pasivo
# Ahora puedes ejecutar: recon_pasivo example.com
```

---

## 💻 Uso

### Sintaxis básica

```bash
./recon_pasivo.sh <dominio>
```

### Ejemplos

```bash
# Reconocimiento simple
./recon_pasivo.sh example.com

# Con dominio subdividido
./recon_pasivo.sh sub.example.com

# Ver logs en tiempo real
./recon_pasivo.sh google.com && cat recon_google.com/recon.log
```

---

## 📊 Estructura de Salida

El script crea una carpeta `recon_<dominio>/` con:

```
recon_example.com/
├── recon.log           # Log detallado de la ejecución
├── robots.txt          # Archivo robots.txt del sitio
├── wayback.txt         # URLs históricas encontradas
└── endpoints.txt       # Endpoints sensibles filtrados
```

### Ejemplo de salida

```
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
    recon.log (2.1K)
```

---

## ✨ Características

### 🔒 Seguridad
- ✅ Validación de dominios con regex
- ✅ Detección de variables no definidas (`set -u`)
- ✅ Manejo de errores en pipes (`set -o pipefail`)
- ✅ Prevención de inyecciones de comandos

### 📝 Logging
- ✅ Log file persistente
- ✅ Salida en pantalla + archivo simultáneamente
- ✅ Contadores de resultados
- ✅ Información de tamaños de archivos

### 🛡️ Robustez
- ✅ Verificación de herramientas antes de ejecutar
- ✅ Manejo gracioso de fallos
- ✅ Validación de archivos antes de procesarlos

---

## 🔧 Solución de Problemas

### ❌ Error: "waybackurls: command not found"

```bash
# Asegúrate de tener Go instalado
go version

# Instala waybackurls
go install github.com/tomnomnom/waybackurls@latest

# Verifica que está en PATH
which waybackurls

# Si no aparece, agrega a .bashrc o .zshrc
export PATH="$PATH:$(go env GOPATH)/bin"
source ~/.bashrc
```

### ❌ Error: "Dominio inválido"

El dominio contiene caracteres no permitidos. Usa solo:
- Letras: `a-z`, `A-Z`
- Números: `0-9`
- Puntos: `.`
- Guiones: `-`

```bash
# ❌ Incorrecto
./recon_pasivo.sh example.com/path

# ✅ Correcto
./recon_pasivo.sh example.com
```

### ⚠️ Sin resultados en Wayback Machine

Algunos dominios nuevos o privados no tienen snapshots. Verifica:
```bash
# Manualmente en el navegador
https://web.archive.org/web/*/example.com
```

### 📝 Ver los logs

```bash
# Log completo
cat recon_example.com/recon.log

# Últimas líneas
tail -f recon_example.com/recon.log
```

---

## ⚖️ Disclaimer Legal

**⚠️ IMPORTANTE**

Este script es solo para:
- ✅ Educación y aprendizaje
- ✅ Pruebas autorizadas en dominios propios
- ✅ Auditorías de seguridad con permiso

**Prohibido:**
- ❌ Usar contra dominios sin autorización
- ❌ Recopilación no autorizada de datos
- ❌ Acceso no autorizado a sistemas

El autor no es responsable de usos malintencionados.

---

## 📄 Licencia

Este proyecto está bajo la licencia **MIT**.

Ver [LICENSE](LICENSE) para más detalles.

---

## 👤 Autor

**antg1203-hash**

- GitHub: [@antg1203-hash](https://github.com/antg1203-hash)
- Repositorio: [recon_pasivo_script.sh](https://github.com/antg1203-hash/recon_pasivo_script.sh)

---

## 🤝 Contribuciones

¡Los PRs son bienvenidos! Para cambios mayores:

1. Fork el repo
2. Crea una rama (`git checkout -b feature/mejora`)
3. Commit tus cambios (`git commit -am 'Add mejora'`)
4. Push a la rama (`git push origin feature/mejora`)
5. Abre un Pull Request

---

## 📞 Soporte

¿Problemas? Abre una [issue](https://github.com/antg1203-hash/recon_pasivo_script.sh/issues)

---

<div align="center">

**⭐ Si te resultó útil, dale una estrella!**

</div>
