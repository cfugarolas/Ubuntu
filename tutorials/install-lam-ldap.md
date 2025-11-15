<div align="center">

  <img src="/img/logo_ubuntu.png" alt="Logo Ubuntu" width="100"/>

# 🐧 Ubuntu LDAP Tutorials
### Instal·lació de LAM (LDAP Account Manager) en un servidor Ubuntu

Aquest tutorial explica com instal·lar i configurar **LDAP Account Manager (LAM)** en un servidor Ubuntu amb LDAP ja actiu.

</div>

---

## 📚 Objectius

- Instal·lar LAM en un servidor Ubuntu amb LDAP
- Configurar LAM per connectar-se al servidor LDAP existent
- Accedir a LAM via navegador web per gestionar usuaris i grups

---

## 📝 1️⃣ Actualitzar el sistema

És recomanable començar actualitzant els paquets del sistema:

```bash
sudo apt update && sudo apt upgrade -y
``

##📥 2️⃣ Instal·lar LDAP Account Manager (LAM)

Instal·lem LAM des dels repositoris oficials d’Ubuntu:

```bash
sudo apt install ldap-account-manager -y
```

##🔧 4️⃣ Configurar LAM per connectar al teu LDAP (Consola)

El fitxer principal de configuració és:

```bash
sudo nano /etc/lam/lam.conf
```

Exemple de configuració bàsica si el teu servidor LDAP és ldap://localhost i l’administrador té el DN cn=admin,dc=mydomain,dc=test:

```bash
$servers = array(
    array(
        'name' => 'Servidor LDAP Local',
        'host' => 'ldap://localhost',
        'port' => 389,
        'base_dn' => 'dc=mydomain,dc=test',
        'bind_dn' => 'cn=admin,dc=mydomain,dc=test',
        'bind_pw' => 'p@ssw0rd'
    )
);
```

⚠️ Substitueix p@ssword amb la contrasenya real del teu administrador LDAP i el teu domini de proves.
Per seguretat, evita deixar la contrasenya en clar si el servidor és públic.
