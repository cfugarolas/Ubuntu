<div align="center">

<img src="/img/logo_ubuntu.png" alt="Logo Ubuntu" width="100"/>

# 🐧 Ubuntu Tutorials  
### Canvi del nom del host i configuració del domini

Petit tutorial per aprendre a canviar el **nom del teu equip** i afegir-li un **domini personalitzat** a Ubuntu.

---

</div>

# 🌐 Canvi de *hostname* i afegir un domini a Ubuntu

Aquest tutorial explica com canviar el **nom del host (hostname)** del sistema i afegir-hi un **domini personalitzat**, com ara `mydomain.test`.  
És una configuració molt útil per a entorns de desenvolupament o laboratoris de proves.

---

## 🧩 Objectiu

Volem que el nostre equip s’identifiqui així:

- **Nom del servidor (hostname):** `server`  
- **Domini:** `mydomain.test`  
- **Nom complet del host (FQDN):** `server.mydomain.test`

---

## 🔍 1. Comprovar el *hostname* actual

Abans de fer canvis, mirem quin nom  i domini té actualment el sistema:

```bash
hostname
hostname -f
```

### ⚙️ 2. Canviar el nom del host

Primer canviem el nom curt del nostre equip amb `hostnamectl`:

```bash
sudo hostnamectl set-hostname server
```

### ⚙️ 3. Editar el fitxer `/etc/hosts`

Ara cal definir el domini i associar-lo al nostre *hostname*.  
Obrim el fitxer amb permisos d’administrador:

```bash
sudo nano /etc/hosts
```

Afegim la següent línia a l'arxiu /etc/hosts

```bash
127.0.0.1   localhost
127.0.1.1   server.mydomain.test server
```
> 💡 **Explicació:**
> 
> - `127.0.0.1` apunta al sistema local (*loopback*).
> - `127.0.1.1` s’utilitza habitualment per al nom de la màquina.
> - Posem primer el **nom complet (FQDN)** i després el **nom curt**.
>
> Desa els canvis amb `Ctrl + O`, prem `Enter` i surt amb `Ctrl + X`.

### ⚙️ 4. Verificar el nom del host i el domini

Comprovem que el canvi s’ha aplicat correctament:

```bash
# Nom curt del host
hostname

# Nom complet (FQDN)
hostname -f
```
---

## ✅ 5. Conclusió

Hem completat la configuració del **hostname** i del **domini local**:

- El nom curt del host és `server`
- El nom complet (FQDN) és `server.mydomain.test`
- La configuració està correcta si:
  ```bash
  hostname      # → server
  hostname -f   # → server.mydomain.test

---

## 🔙 Veure tots els tutorials d'UBUNTU

[📖 Veure tots els tutorials d'Ubuntu](../README.md)
