<div align="center"> 
  
  <img src="/img/logo_ubuntu.png" alt="Logo Ubuntu" width="100"/>

# 🐧 Ubuntu Tutorials
### Instal·lació i configuració bàsica d’OpenLDAP a Ubuntu

Petit tutorial per aprendre a instal·lar, configurar i verificar un servidor LDAP en Ubuntu.

</div>

---

## 📚 Instal·lació d’OpenLDAP en Ubuntu

Aquest tutorial explica com instal·lar i configurar un servidor LDAP en Ubuntu.
Veurem:

- Instal·lació de paquets necessaris.
- Configuració inicial.
- Comprovar el funcionament del servei.

## 🧩 Objectiu

- Instal·lar OpenLDAP i el paquet d’utilitats.
- Configurar les dades bàsiques del directori LDAP.
- Verificar que el servei funciona correctament.

## 🔍 1. Actualitzar el sistema

Sempre comencem actualitzant els repositoris i paquets, podeu mirar el tutorial d'actualització.
[📖 Actualitzar completament el sistema Ubuntu](../tutorials/actualitzacions-sistema.md)

## 🌐 2. Configurar el nom i el domini configurat
Configurarem el nom i l’extensió del domini que vulguem utilitzar al nostre LDAP. Podeu consultar el tutorial.

Canviar el nom del host (hostname) del sistema i afegir-hi un domini personalitzat.
[📖Canvi de hostname i afegir un domini a Ubuntu](../tutorials/canvi-hostname.md)

## 🛜 3. Configurar els adaptadors

Configurar dos adaptadors, un amb xarxa NAT i l'altre com anfitrió. Podeu consultar el tutorial.

[📖Configuració d'adaptadors de xarxes a VirtualBox en Ubuntu](../tutorials/configuracio-xarxa.md)

## 📦 4. Instal·lar OpenLDAP i eines

Instal·lem el servidor i les utilitats administratives:

```bash
sudo apt install slapd ldap-utils -y
```
Durant la instal·lació et demanarà una contrasenya per l’admin LDAP.

**🔐 Recorda-la! La necessitaràs per gestionar el directori.**

## ⚙️ 5. Configuració posterior a la instal·lació

Per reconfigurar els paràmetres inicials:

```bash
sudo dpkg-reconfigure slapd
```

| Pregunta                       | Recomanació       |
| --------------------           | ----------------- |
| Ometre configuració?           | **No**            |
| Nom de domini (DNS)            | mydomain.test     |
| Nom d’organització             | El meu domini     |
| Contrasenya de l'administrador | password          |
| Esborrar BD antiga?            | yes               |
| Moure BD antiga ?              | yes               |

## 🧾 6. Comprovar l’estat del servei

Verifiquem si LDAP està actiu:

```bash
sudo systemctl status slapd
```
Si està funcionant, hauràs de veure:

✅ **active (running)**

## 🧪 7. Consultar el directori LDAP

Fem una consulta de prova:

```bash
ldapsearch -x -LLL -H ldap:/// -b dc=mydomain,dc=test
```

Canvia mydomain i test pels valors que hagis posat.

Si es mostra informació, l’LDAP funciona correctament ✅

## 🛑 8. Aturar o reiniciar el servei LDAP

Per reiniciar:

```bash
sudo systemctl restart slapd
```

Per aturar:
```bash
sudo systemctl stop slapd
```

## ✅ 8. Conclusió

Has instal·lat correctament el servidor OpenLDAP.

- El servei està configurat i funcionant.
- Consultar el directori.

Aquest és un punt de partida ideal per entorns d’autenticació d’usuaris.

---

## 🔙 Veure tots els tutorials d'UBUNTU

[📖 Veure tots els tutorials d'Ubuntu](../README.md)
