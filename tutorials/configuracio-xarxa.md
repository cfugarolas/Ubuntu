<div align="center">

<img src="/img/logo_ubuntu.png" alt="Logo Ubuntu" width="100"/>

# 🐧 Ubuntu Tutorials  
### Configuració de xarxes a VirtualBox

Petit tutorial per aprendre a configurar **adaptadors de xarxa NAT i Host-only** a una màquina Ubuntu dins de VirtualBox.

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

