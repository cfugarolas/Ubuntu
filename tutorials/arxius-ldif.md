<div align="center"> 
  
  <img src="/img/logo_ubuntu.png" alt="Logo Ubuntu" width="100"/>

# 🐧 Ubuntu Tutorials
### Creació d’Unitats Organitzatives amb arxius .ldif

Tutorial per aprendre a crear i importar objectes al directori LDAP utilitzant fitxers `.ldif`.

</div>

---

# 📘 Introducció

En aquest tutorial aprendrem:

- Què és un fitxer `.ldif`
- Com crear un fitxer `.ldif` des de zero
- Com definir dues Unitats Organitzatives (OUs): **users** i **groups**
- Com importar aquest fitxer al nostre servidor LDAP
- Com verificar que la importació ha funcionat

Aquest és un procés fonamental per preparar l’estructura bàsica d’un directori LDAP.

---

# 📂 Què és un fitxer `.ldif`?

Un fitxer `.ldif` (*LDAP Data Interchange Format*) és un arxiu de text que conté definicions d’objectes LDAP.

S’utilitza per:

- Crear objectes al directori
- Modificar-los
- Importar o exportar dades

Cada entrada `.ldif` representa un objecte i sempre inclou:

- Un **DN** (Distinguished Name)
- Classes d’objecte (*objectClass*)
- Atributs de l’objecte

---

# 🗂️ Creació de les Unitats Organitzatives *users* i *groups*

## 1️⃣ Crear el fitxer `.ldif`

Obrirem un nou fitxer anomenat **OUs.ldif**:

```bash
sudo nano OUs.ldif
```

## 2️⃣ Afegir el contingut LDIF

Copia i enganxa el següent contingut al teu fitxer `.ldif`:

```bash
dn: ou=users,dc=elmeudomini,dc=test
ou: users
objectClass: top
objectClass: organizationalUnit

dn: ou=groups,dc=elmeudomini,dc=test
ou: groups
objectClass: top
objectClass: organizationalUnit
```
