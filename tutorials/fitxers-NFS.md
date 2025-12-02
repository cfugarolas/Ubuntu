<div align="center">

<img src="/img/logo_ubuntu.png" alt="Logo Ubuntu" width="100"/>

# 🐧 Ubuntu Tutorials  
### Compartició de fitxers Linux: NFS

Tutorial per aprendre a **instal·lar i configurar els servei NFS (Network File System)**, aplicant totes les configuracions necessaries.

---

</div>

# 🔄 Compartició de fitxers Linux: NFS

Tutorial per aprendre a **instal·lar i configurar els servei NFS (Network File System)**, aplicant totes les configuracions necessaries.

---

### 🧩 Objectiu

- Instal·lació del servei. 
- Creació recurs compartit.  
- Configurar NFS.  
- Accés des del client.

---

### 1️⃣ Instal·lació del servei

La primera activitat serà instal·lar el servidor NFS i totes les dependències.

```bash
sudo apt install nfs-kernel-server
```

### 2️⃣Creació recurs compartit

Primer de tot crearem una carpeta compartida dins el directori /srv,

```bash
sudo mkdir /srv/compartida
```

li treurem la propietat a qualsevol usuari i grup

```bash
sudo chown nobody:nogroup /srv/compartida
```

i donem tots els permisos 1(executat)+2(escriure)+4(lectura)

```bash
sudo chmod -R 777 /srv/compartida
```

### 3️⃣ Configuració NFS

Editarem l'arxiu de configuració /etc/exports amb el nano

```bash
sudo nano /etc/exports
```

Afegim la següent configuració

```bash
/srv/compartida *(rw,sync,no_subtree_check)
```
Format de configuració

        ruta client1(opcions)

**Formats per definir els hosts**

| Format host (client1)| Exemple | Explicació |
|-------------|---------|------------|
| **IP única** | `192.168.1.50` | Només aquest equip pot muntar el recurs. |
| **Diverses IPs** | `192.168.1.10 192.168.1.11` | Permet accés a diversos equips concrets. |
| **Subxarxa (CIDR)** | `192.168.1.0/24` | Permet accés a tots els equips de la subxarxa 192.168.1.x. (el mètode més recomanat). |
| **Nom de host** | `pc-alumne.local` | El servidor resol el nom via DNS o /etc/hosts. |
| **Tots els hosts** | `*` | Qualsevol equip pot accedir al recurs. Només en entorns controlats. |
| **Rang d’IP (menys habitual)** | `192.168.1.100-192.168.1.150` | Permet un bloc d’adreces específic (pot no estar suportat en tots els servidors). |


| Opcions                   | Explicació     |
| --------------------           | ----------------- |
|rw            | Read and write           |
|ro            |Read only    |
|sync          | El servidor escriu les dades a disc abans de respondre al client.          |
|async        | El servidor no escriu immediatament a disc; pot mantenir dades en memòria i respondre al client abans de guardar-les.   |
|no_subtree_check           |No comprova subdirectoris, és més ràpid però més insegur  |
|root_squash         |No manté els privilegis de root quan es connencta un recurs remot  |

### 4️⃣ Iniciar el servei

```bash
systemctl start nfs-kernel-server
```

### 5️⃣ Comprovacions

Verificar que estem compartint via NFS

```bash
exportfs -u
```

Podem veure amb **rpcinfo -p <ip>** com el servei està connectat i usant el port 20249

```bash
rpcinfo -p 10.0.2.5
```

Per verificar el funcionament crearem dos arxius a dins la carpeta compartida, un com l'usuari normal i l'altre com a root

```bash

cd /srv/compartida
sudo touch fitxerroot.txt
touch fitxerusuari.txt
```

Verificació dels permisos

```bash
ls -l
```
### 6️⃣ Accés des del client

Primer de tot haurem de instal·lar el client nfs al nostre client Ubunto Desktop / Zorin

```bash
apt install nfs-common
```

Ara des del client verifiquem que tenim accés al recurs del servidor

```bash
Format:
showmount -e <ip_nostre_servidor>

Exemple:
showmount -e 10.0.2.5
```

Sortida:
```
Export list for 10.0.2.5:
/srv/compartida *
```

### 7️⃣Muntatge carpeta compartida al client

En el sistema linux qualsevol recurs extern, s'ha de mapejar sobre una carpeta, per tant, el primer es crear aquesta carpeta,

```bash
sudo mkdir /srv/remot
```

ara per poder accedir al recurs, utilitzarem la comanda mount

```bash
sudo mount -t nfs 10.0.2.5:/srv/compartida /srv/remot
```




