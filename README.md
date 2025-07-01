# M117

# Netzwerkübersicht & Dokumentation – WG "La familia"

## 📦 Materialien für Gigabit-Ethernet (1000 MBit/s)

### 1. Patchkabel (flexibel)
**Typ:** Cat6a S/FTP (Litze)  
**Eigenschaften:**
- Frequenzbereich bis 500 MHz
- 4x2xAWG26/7 (feindrähtig)
- Doppelt geschirmt: Folie + Geflecht
- Halogenfreier LSZH-Mantel
- Ideal für mobile Verbindungen

**Bezugsquelle:** Reichelt Elektronik  
**Artikelnummer:** `NETL CAT6A-10`  
**Kosten:** `1,95 €/m`

---

### 2. Installationskabel (fest)
**Typ:** Cat6a U/FTP (Massivdraht)  
**Eigenschaften:**
- Frequenzbereich bis 500 MHz
- 4x2xAWG23/1 (Massivleiter)
- Paarweise Folienabschirmung
- PE-Isolierung
- Für feste Gebäudeverkabelung geeignet

**Bezugsquelle:** Conrad Electronic  
**Artikelnummer:** `CONN-CAT6A-305`  
**Kosten:** `0,85 €/m` (bei 305 m-Rolle)

---

## 🌐 IP-Adressen und Subnetting

### Private IPv4-Adressbereiche
| Bereich               | Klasse früher | Beschreibung                 |
|----------------------|---------------|------------------------------|
| 10.0.0.0 – 10.255.255.255     | A             | Große Netzwerke              |
| 172.16.0.0 – 172.31.255.255   | B             | Mittlere Netzwerke           |
| 192.168.0.0 – 192.168.255.255 | C             | Heim- und Büronetzwerke      |

**Sonderadressen:**
- `127.0.0.1` – Loopback-Adresse (localhost)
- `169.254.0.0/16` – APIPA (bei DHCP-Ausfall)

---

### Subnetzberechnungen: Beispiel IP `10.11.12.4`

| Präfix | Netzmaske        | Netzadresse   | Broadcast         | Host-Anteil     |
|--------|------------------|---------------|-------------------|-----------------|
| /24    | 255.255.255.0    | 10.11.12.0    | 10.11.12.255      | Host-ID: 4      |
| /16    | 255.255.0.0      | 10.11.0.0     | 10.11.255.255     | Host-ID: 12.4   |
| /8     | 255.0.0.0        | 10.0.0.0      | 10.255.255.255    | Host-ID: 11.12.4|

---

### Anzahl möglicher Hosts

| Subnetz     | Bereich                   | Nutzbare Hosts      |
|-------------|---------------------------|----------------------|
| 10.0.0.0/8  | 10.0.0.1 – 10.255.255.254 | 16.777.214 Hosts     |
| 10.0.0.0/16 | 10.0.0.1 – 10.0.255.254   | 65.534 Hosts         |
| 10.0.0.0/24 | 10.0.0.1 – 10.0.0.254     | 254 Hosts            |

---

### Subnetzvergleich – Kommunikation möglich?

| Paar | Kommunikation | Grund                                           |
|------|---------------|--------------------------------------------------|
| 1    | ✅ Ja         | Beide im gleichen Subnetz (192.168.1.0/24)      |
| 2    | ✅ Ja         | Beide im gleichen Subnetz (192.168.0.0/16)      |
| 3    | ❌ Nein       | Unterschiedliche Subnetze                       |
| 4    | ✅ Ja         | Beide im Netz 10.0.0.0/8                         |

---

### Weitere Subnetz-Fälle

| Paar | Kommunikation | Grund                                      |
|------|---------------|---------------------------------------------|
| 1    | ❌ Nein       | Unterschiedliche Masken (/8 vs. /24)        |
| 2    | ❌ Nein       | Ungültige IP (258 ist kein gültiges Oktett) |
| 3    | ✅ Ja         | Beide im Netz 172.0.0.0/8                    |
| 4    | ❌ Nein       | Unterschiedliche Subnetze                   |

---

## 🧠 Netzwerkwissen kompakt

### Ports & Dienste

| Dienst  | Beschreibung                              | Port |
|---------|-------------------------------------------|------|
| HTTP    | Web unverschlüsselt                       | 80   |
| HTTPS   | Web verschlüsselt                         | 443  |
| FTP     | Dateiübertragung                          | 21   |
| SMTP    | Mail senden                               | 25   |
| POP3    | Mail empfangen                            | 110  |
| IMAP    | Mail auf Server verwalten                 | 143  |
| DNS     | Namensauflösung                           | 53   |
| Echo    | Ping-Test                                 | 7    |

**Portbereiche:**
- Well-known Ports: `0–1023`
- Registered Ports: `1024–49151`
- Dynamic/Private Ports: `49152–65535`

---

### Pfade & Dateisysteme

**Absoluter Pfad:**  
Vollständige Angabe (z. B. `C:\Users\Max\Datei.txt`)

**Relativer Pfad:**  
Bezogen auf aktuelles Verzeichnis (z. B. `..\Bilder\foto.jpg`)

**FAT vs. NTFS:**

| System | Vorteile                         | Nachteile                       |
|--------|----------------------------------|---------------------------------|
| FAT32  | Hohe Kompatibilität              | Keine Rechte, 4GB-Grenze        |
| NTFS   | Rechteverwaltung, Verschlüsselung| Geringere Kompatibilität        |

---

### Benutzer & Rechteverwaltung

- **Accounting:** Wer hat was wann getan?
- **Gruppenrechte:** Einfacher & sicherer verwalten
- **Lokal:** Für Einzel-PCs geeignet
- **Zentral (z. B. AD):** Für Netzwerke mit vielen Usern

**Vererbung:** Rechte vom Hauptordner auf Unterordner übertragen

**UNC-Pfad-Beispiel:** `\\10.0.1.100\projekte2024`

---

## 🔐 Sicherheit

**USB-Stick verloren (FAT32):**  
→ Sofort Maßnahmen: Passwörter ändern, Bank informieren, Cloud-Zugänge prüfen

**NTFS-Stick:**  
→ Schutz nur bei richtiger Konfiguration (z. B. BitLocker, Rechte)

---

## 🏢 Subnetting bei „Muster GmbH“

**Ausgangsnetz:** `10.0.0.0/16`  
→ Aufteilung in neun /24-Subnetze (A–I)

| Subnetz | Netzadresse | Broadcast     | Gateway      |
|---------|-------------|---------------|--------------|
| A       | 10.0.0.0    | 10.0.0.255    | 10.0.0.1     |
| B       | 10.0.1.0    | 10.0.1.255    | 10.0.1.1     |
| …       | …           | …             | …            |
| I       | 10.0.8.0    | 10.0.8.255    | 10.0.8.1     |

**PC-Konfiguration Beispiel:**

| PC      | Subnetz | IP-Adresse  | Gateway    |
|---------|---------|-------------|------------|
| A-PC1   | A       | 10.0.0.2    | 10.0.0.1   |
| B-PC2   | B       | 10.0.1.3    | 10.0.1.1   |
| C-PC2   | C       | 10.0.2.3    | 10.0.2.1   |

---

## 🧪 Wireshark & Netzwerkdiagnose

### Wichtige Filter:
- **ICMP (Ping):** `icmp`
- **DNS-Abfragen:** `dns`
- **DHCP:** `bootp`
- **HTTP:** `http`
- **HTTPS (TLS):** `ssl.handshake.extensions_server_name`

### Lokale IP & Router-IP herausfinden:
- Windows: `ipconfig`
- Linux/Mac: `ip route | grep default`

### DNS-Server anzeigen:
- Windows: `ipconfig /all`
- Linux/Mac: `cat /etc/resolv.conf`

---

### Beispiel: HTTP vs. HTTPS (Webzugriff)

**HTTP (Port 80):**
- Sichtbar: GET-Request, IP-Adressen, MAC-Adressen, Daten

**HTTPS (Port 443):**
- Verschlüsselt: Nur SNI, Zertifikate und Handshake sichtbar

---

> 📅 Letzte Aktualisierung: 01.07.2025  
> Autor: Deine IT-AG der WG „La familia“
