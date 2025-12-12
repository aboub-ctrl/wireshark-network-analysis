# Analyse de Trafic Réseau avec Wireshark

## 🎯 Objectif
Premier projet pratique d'analyse de trafic réseau. Apprendre à capturer et filtrer des paquets pour comprendre les protocoles réseau.

## 🛠️ Environnement
- **OS :** Ubuntu Linux
- **Outil principal :** Wireshark
- **Outil secondaire :** Nmap

## 📋 Méthodologie

### 1. Installation et configuration
```bash
sudo apt update
sudo apt install wireshark -y
sudo usermod -aG wireshark $USER
```

### 2. Capture de trafic
- Lancement de Wireshark
- Sélection de l'interface réseau active
- Démarrage de la capture
- Navigation sur neverssl.com pour générer du trafic HTTP
- Arrêt et sauvegarde de la capture

### 3. Analyse avec filtres

#### Filtre HTTP
```
![filtr_http](https://github.com/user-attachments/assets/b5b689c6-5504-46c2-b4e4-374ee86750fe)
![analyse_paquet_http](https://github.com/user-attachments/assets/1c6a1791-948b-4fa0-b371-dbc8d7e266b3)

http
```
**Observation :** Trafic HTTP non chiffré capturé depuis neverssl.com. Les requêtes et réponses sont visibles en clair.

#### Filtre DNS
```
![filtre_DNS](https://github.com/user-attachments/assets/f3fcb306-1c9f-4dec-a92e-67eb73258a19)
![analyse_du_paquet avec le protocol_DNS](https://github.com/user-attachments/assets/f968988c-2f19-4710-a4fe-e91afa82af38)

dns
```
**Observation :** Requêtes de résolution de noms de domaine. Montre comment le navigateur traduit les URL en adresses IP.

#### Filtre TLS
```
![analyse_dun_paquet_protocol_Tls](https://github.com/user-attachments/assets/54814fe8-b726-4cc9-a3c3-b6eb7c6c9e8f)

![filtre_Tls](https://github.com/user-attachments/assets/1e60aa32-be62-4644-acb4-d7d379ab8a6d)

tls
```
**Observation :** Trafic HTTPS chiffré. Contrairement à HTTP, le contenu des données est protégé par chiffrement.

#### Filtre paquets SYN
```
![analyse_du_paquet_syn](https://github.com/user-attachments/assets/798b7992-bc02-4ffc-afa4-e397f8393d1e)

tcp.flags.syn == 1 && tcp.flags.ack == 0
```
**Observation :** Paquets d'initiation de connexion TCP sans accusé de réception.

### 4. Scan de ports local
```bash
nmap localhost
```
Scan des ports ouverts sur la machine locale pour observer les paquets générés dans Wireshark.

## 🔍 Résultats et apprentissages

### Différence HTTP vs HTTPS
- **HTTP (neverssl.com)** : Données visibles en clair dans Wireshark
- **HTTPS** : Données chiffrées, seules les métadonnées (IP, ports) sont visibles
- **Importance** : Nécessité d'utiliser HTTPS pour protéger les données sensibles

### Protocoles observés
- DNS pour la résolution de noms
- TCP pour l'établissement de connexions
- HTTP pour le transfert de données web non chiffré
- TLS pour les connexions sécurisées

### Analyse de paquets SYN
![analyse_du_paquet_syn](https://github.com/user-attachments/assets/cc0ee115-a445-4faf-851b-9580bf5c02e1)

Les paquets SYN correspondent à la première étape du "three-way handshake" TCP. Leur observation permet de comprendre comment les connexions réseau s'établissent.

## 🎓 Compétences développées
- Installation et configuration de Wireshark
- Capture de trafic réseau
- Utilisation de filtres pour isoler des protocoles
- Compréhension pratique de HTTP, DNS, TCP, TLS
- Utilisation de nmap pour générer du trafic
- Analyse basique de paquets réseau
---
*Projet réalisé dans le cadre de ma formation en Ingénierie Réseaux et Systèmes*
