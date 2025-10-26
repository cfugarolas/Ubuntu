<div align="center">

<img src="/img/logo_ubuntu.png" alt="Logo Ubuntu" width="100"/>

# 🐧 Ubuntu Tutorials  
### Configuració de xarxes a VirtualBox

Petit tutorial per aprendre a configurar **adaptadors en NAT i Host-only** a una màquina Ubuntu dins de VirtualBox.

---

</div>

# 🌐 Configuració d'adaptadors de xarxa a Ubuntu en VirtualBox

Aquest tutorial explica com configurar la xarxa de la màquina virtual Ubuntu dins de VirtualBox.  
Aprendrem a configurar:

- NAT (Network Address Translation) per accés a Internet.
- Xarxa d’amfitrió (Host-only) per comunicació amb el host sense Internet.

---

## 🧩 Objectiu

- Configurar **adaptador NAT** per tenir connexió a Internet.
- Configurar **adaptador Host-only** per tenir una xarxa local amb el host.
- Assignar IP fixa a Ubuntu per l’adaptador Host-only.

---

## 🔍 1. Comprovar adaptadors de xarxa actuals

Primer, mirem quins adaptadors té la VM Ubuntu:

```bash
ip a
```
💡 Això mostra les interfícies de xarxa actuals (**enp0s3**, **enp0s8**, etc.) i si tenen IP assignada.

**Tipus d’interfícies habituals en VirtualBox:**

| Interfície | Tipus       | Exemple IP      | Servei                 |
|------------|------------|----------------|-----------------------|
| enp0s3     | NAT        | 10.0.2.15      | Internet via host      |
| enp0s8     | Host-only  | 192.168.56.101 | Xarxa amb el host      |


## ⚙️ 2. Configurar VirtualBox

Apaga la màquina virtual.

Obre VirtualBox, selecciona la VM Ubuntu → Settings → Network.

Configura els adaptadors:

🛜 Adaptador 1
- Activat: ✅
- Adjunt a: NAT (Serveix per donar connexió a Internet a la VM.)

🛜 Adaptador 2 – Host-only (Serveix per comunicar la VM amb l’amfitrió sense exposar-la a Internet.)
- Activat: ✅
- Adjunt a: Host-only Adapter

**💡Recorda:**  pots activar Cable Connected per assegurar-te que la VM detecta la interfície.

## ⚙️ 3. Configurar Ubuntu per DHCP (Netplan)

Editar l'arxiu Netplan com a sudo:

```bash
sudo nano /etc/netplan/50-cloud-init.yaml
```
Exemple de configuració per dos adaptadors amb DHCP:

```bash
network:
  version: 2
  ethernets:
    enp0s3:
      dhcp4: true
    enp0s8:
      dhcp4: true
```
Aplica els canvis:

```bash
sudo netplan apply
```
## 🔍 4. Verificar les IP assignades

```bash
ip a
```

- **enp0s3** → IP automàtica per NAT (normalment 10.0.2.x) → Internet
- **enp0s8** → IP automàtica per Host-only (normalment 192.168.56.x) → comunicació amb el host

Comprova connexió:

```bash
ping -c 4 8.8.8.8 -c4 # NAT → Internet
```
On xxx  (.101, .102, .103, ...) és l’adreça IP assignada a l’adaptador Host-only.

```bash
ping -c 4 192.168.56.xxx  # Host-only → Host
```

**💡 Explicació:**

- DHCP facilita la configuració automàtica d’IP, gateway i DNS.
- No cal assignar IP fixa manualment, però la IP pot canviar cada vegada que la VM s’inicia.

## ✅ 5. Conclusió

- La VM Ubuntu té Internet via NAT amb IP assignada automàticament.
- Té comunicació amb el host via Host-only també amb DHCP.
- La configuració és ràpida i senzilla per proves o laboratoris.

---

## 🔙 Veure tots els tutorials d'UBUNTU

[📖 Veure tots els tutorials d'Ubuntu](../README.md)

