# Benutzerhandbuch – MQ6 Adressverwaltung Web-App

**Version:** 1.0
**Stand:** März 2026
**Anwendung:** `Adressen_WebApp.html`

---

## Inhaltsverzeichnis

1. [Übersicht](#1-übersicht)
2. [Systemvoraussetzungen & Start](#2-systemvoraussetzungen--start)
3. [Die Benutzeroberfläche im Überblick](#3-die-benutzeroberfläche-im-überblick)
4. [Toolbar – die Werkzeugleiste](#4-toolbar--die-werkzeugleiste)
5. [Adressliste – die Seitenleiste](#5-adressliste--die-seitenleiste)
6. [Adressformular – Identifikation](#6-adressformular--identifikation)
7. [Adressformular – Adressdaten](#7-adressformular--adressdaten)
8. [Adressformular – Unternehmensspezifikation](#8-adressformular--unternehmensspezifikation)
9. [Gruppenfelder](#9-gruppenfelder)
   - [9.1 Kunde](#91-reiter-kunde)
   - [9.2 Lieferant](#92-reiter-lieferant)
   - [9.3 Personal](#93-reiter-personal)
   - [9.4 Sonstiges](#94-reiter-sonstiges)
10. [Untertabellen](#10-untertabellen)
    - [10.1 Kommunikation](#101-kommunikation)
    - [10.2 Ansprechpartner](#102-ansprechpartner)
    - [10.3 Bankkonten](#103-bankkonten)
    - [10.4 Konditionen](#104-konditionen)
    - [10.5 Suchbegriffe](#105-suchbegriffe)
    - [10.6 Beziehungen](#106-beziehungen)
    - [10.7 Infomerkmale](#107-infomerkmale)
11. [Suche und Filter](#11-suche-und-filter)
12. [Lesezeichen](#12-lesezeichen)
13. [Datenspeicherung](#13-datenspeicherung)
14. [Tastaturkürzel](#14-tastaturkürzel)
15. [Häufige Fragen (FAQ)](#15-häufige-fragen-faq)

---

## 1. Übersicht

Die **MQ6 Adressverwaltung Web-App** ist eine browserbasierte Anwendung zur Verwaltung von Geschäftspartnern (Kunden, Lieferanten, Personal u. a.). Sie basiert auf den Feldern und Konzepten des T4-ERP-Systems der TETRA GmbH und ist als eigenständige HTML-Datei konzipiert – ohne Installation, ohne Server, ohne Internetzugang.

### Was kann die Anwendung?

- Adressen anlegen, bearbeiten und löschen
- Adressen als Kunde, Lieferant, Mitarbeiter oder sonstige Kontakte klassifizieren
- Kommunikationsdaten (Telefon, E-Mail, Website …) hinterlegen
- Ansprechpartner, Bankverbindungen und Zahlungskonditionen verwalten
- Suchbegriffe, Beziehungen und individuelle Infomerkmale erfassen
- Adressen nach Name, Ort, Nummer oder Gruppe suchen und filtern
- Favoriten (Lesezeichen) markieren
- Alle Daten dauerhaft im Browser speichern

---

## 2. Systemvoraussetzungen & Start

### Voraussetzungen

| Anforderung | Details |
|---|---|
| **Browser** | Google Chrome, Microsoft Edge, Firefox oder Safari (aktuelle Version) |
| **Internetzugang** | Nur beim ersten Laden (für Bootstrap und Vue.js CDN) |
| **Installation** | Keine – die Anwendung ist eine einzelne HTML-Datei |

> **Hinweis:** Beim ersten Öffnen lädt die Anwendung Bootstrap 5 und Vue 3 aus dem Internet. Bei wiederholtem Öffnen werden diese Bibliotheken aus dem Browser-Cache geladen – ein Internetzugang ist dann nicht mehr zwingend erforderlich.

### Anwendung starten

Doppelklick auf die Datei `Adressen_WebApp.html` – die Anwendung öffnet sich im Standard-Browser.

Beim ersten Start sind **6 Demo-Datensätze** vorgeladen, damit die Oberfläche direkt erkundbar ist.

---

## 3. Die Benutzeroberfläche im Überblick

```
┌──────────────────────────────────────────────────────────────────┐
│  TOOLBAR  [Neu] [Speichern] [Löschen] [Suche] [Lesezeichen] ←/→ │
├────────────────┬─────────────────────────────────────────────────┤
│                │  IDENTIFIKATION                                  │
│  ADRESSLISTE   │  Adress-Nr. | Kunden-Nr. | Lief.-Nr. | HR-Nr.  │
│                ├──────────────────┬──────────────────────────────┤
│  🔍 Suche      │  ADRESSDATEN     │  SPEZIFIKATION + GRUPPEN     │
│  [Alle][K][L]  │  Anrede, Name    │  Betriebstyp, Branche …      │
│                │  Straße, PLZ     │  ┌─Kunde─┬─Lief.─┬─Perso─┐  │
│  📁 Müller GmbH│  Ort, Nation     │  │ Felder der Gruppe       │  │
│  🚚 Technik AG │                  │  └───────────────────────┘  │
│  👤 Schneider  ├──────────────────┴──────────────────────────────┤
│  📁 Weber GmbH │  [Kom.][Ansp.][Bank][Kond.][Such.][Bez.][Info] │
│  👤 Hoffmann   │  ┌────────────────────────────────────────────┐ │
│  📁 DataTech   │  │  UNTERTABELLE (je nach aktivem Reiter)     │ │
│                │  └────────────────────────────────────────────┘ │
├────────────────┴─────────────────────────────────────────────────┤
│  STATUSLEISTE  ● Gespeichert  | Nr: 100001 | Müller & Co. GmbH  │
└──────────────────────────────────────────────────────────────────┘
```

Die Oberfläche besteht aus vier Bereichen:

| Bereich | Beschreibung |
|---|---|
| **Toolbar** (oben) | Aktionsschaltflächen und Navigation |
| **Adressliste** (links) | Übersicht aller Adressen mit Suche und Filter |
| **Adressformular** (Mitte/rechts) | Detailansicht und Bearbeitung des gewählten Datensatzes |
| **Statusleiste** (unten) | Zeigt Speicherstatus, Adress-Nr. und Name des aktiven Datensatzes |

---

## 4. Toolbar – die Werkzeugleiste

Die Toolbar befindet sich am oberen Rand der Anwendung.

| Schaltfläche | Tastenkürzel | Funktion |
|---|---|---|
| **Neu** | `Strg+N` | Legt einen neuen, leeren Adressdatensatz an |
| **Speichern** | `Strg+S` | Speichert alle Änderungen am aktuellen Datensatz dauerhaft |
| **Löschen** | – | Löscht den aktuell angezeigten Datensatz (nach Bestätigung) |
| **Suche** | `Strg+F` | Setzt den Fokus in das Suchfeld der Adressliste |
| **Lesezeichen** | – | Markiert die aktuelle Adresse als Favorit (⭐) oder hebt die Markierung auf |
| **← Zurück** | – | Wechselt zum vorherigen Datensatz in der gefilterten Liste |
| **→ Vor** | – | Wechselt zum nächsten Datensatz in der gefilterten Liste |

> **Tipp:** Die Schaltfläche **Speichern** ist ausgegraut, solange keine ungespeicherten Änderungen vorliegen. Sobald Sie etwas ändern, wird sie aktiv und die Statusleiste zeigt einen gelben Punkt.

---

## 5. Adressliste – die Seitenleiste

Die linke Seitenleiste zeigt alle vorhandenen Adressen und bietet Filtermöglichkeiten.

### Aufbau eines Listeneintrags

```
📁  Müller & Co. GmbH          [K]
    100001 · 53111 Bonn
```

| Element | Bedeutung |
|---|---|
| **Symbol** | 📁 Firma / 👤 Person / 🚚 Lieferant / 👔 Personal |
| **🔒** (rot) | Datensatz ist gesperrt |
| **⭐** (gelb) | Datensatz ist als Lesezeichen markiert |
| **K** (blau) | Adresse ist als Kunde klassifiziert |
| **L** (grün) | Adresse ist als Lieferant klassifiziert |
| **P** (gelb) | Adresse ist als Personal klassifiziert |

### Suche

Geben Sie im Suchfeld einen Suchbegriff ein. Die Liste filtert sich sofort nach:
- **Name** der Adresse
- **Adress-Nummer**
- **Ort** und **PLZ**
- **Suchbegriffen** aus der Untertabelle „Suchbegriffe"

### Gruppenfilter

Mit den Schaltflächen unterhalb der Suche schränken Sie die Liste weiter ein:

| Schaltfläche | Zeigt |
|---|---|
| **Alle** | Alle Adressen |
| **Kunden** | Nur Adressen mit einer Kundenzuordnung |
| **Lief.** | Nur Adressen mit einer Lieferantenzuordnung |
| **Perso** | Nur Adressen mit einer Personalzuordnung |

---

## 6. Adressformular – Identifikation

Der oberste Bereich des Formulars enthält die eindeutigen Identifikationsnummern des Datensatzes.

| Feld | Pflicht | Beschreibung |
|---|:---:|---|
| **Adress-Nr.** | ✅ | Eindeutige Kennung der Adresse. Wird beim Anlegen automatisch vorgeschlagen. |
| **Kunden-Nr./GLN** | | Vom Kunden vorgeschriebene eigene Nummer oder GLN/ILN (Global Location Number). Bleibt das Feld leer, wird automatisch die Adress-Nr. als Kunden-Nr. verwendet. |
| **Lieferanten-Nr.** | | Die Ihnen vom Lieferanten mitgeteilte Kunden-Nr. bei diesem Lieferanten (also Ihre eigene Nummer beim Lieferanten). |
| **HR-Nr.** | | Handelsregisternummer inkl. Gerichtsstand, z. B. `HRB 12345 Bonn`. |
| **USt-Nr.** | | Umsatzsteuer-Identifikationsnummer. Besonders wichtig bei gewerblichen EU-Auslandspartnern, damit Rechnungen ohne Steuer erstellt werden können. |

---

## 7. Adressformular – Adressdaten

### Anrede

Die Anrede steuert die Sprache, Steuerart und Form der Korrespondenz. Wählen Sie passend aus:

| Gruppe | Einträge | Verwendung |
|---|---|---|
| **Juristische Personen** | Firma, Institution, Verband/Behörde | Unternehmen, Organisationen |
| **Natürliche Personen** | Herr, Frau, Divers, Familie … | Privatpersonen, Einzelpersonen |
| **English** | Mr., Mrs., Ms., Company | Englischsprachige Partner |

> Die Wahl zwischen juristischer und natürlicher Person beeinflusst die steuerliche Behandlung (Netto-/Brutto-Fakturierung).

### Weitere Adressfelder

| Feld | Beschreibung |
|---|---|
| **Name** | Bei Firmen: vollständige Unternehmensbezeichnung mit Rechtsform. Bei Personen: Eingabe in der Reihenfolge Titel, Vorname, Adelsprädikat, Nachname. |
| **Straße / Hausnummer** | Straße und Hausnummer im selben Feld, getrennt durch Leerzeichen. |
| **PLZ** | Postleitzahl ohne Länderkennung (also `53111` statt `D-53111`). Bei US-Adressen: State + Zip im PLZ-Feld, z. B. `CA 95043`. |
| **Ort** | Ortsbezeichnung ohne Land oder sonstige Zusätze. |
| **Postfach** | Nur die Postfachnummer ohne den Titel „Postfach" (wird bei der Ausgabe automatisch ergänzt). |
| **Pf-PLZ** | PLZ des Postfachs, falls abweichend von der Straßenadresse. |
| **Nation** | Land der Adresse. Wird vorbelegt mit dem eigenen Standort. Bei Auslandsadressen erscheint ein 🌐-Symbol. |

---

## 8. Adressformular – Unternehmensspezifikation

Dieser Abschnitt dient der Klassifizierung des Unternehmens für Auswertungen und Mailings.

| Feld | Beschreibung |
|---|---|
| **Betriebstyp** | Grobe Einordnung: Produktion, Handel, Dienstleistung, Handwerk |
| **Branche** | Standardisierte Branchenzuordnung aus der Auswahlliste (z. B. IT / Software, Maschinenbau) |
| **Umsatz (€)** | Angenäherter Jahresumsatz des *Geschäftspartners* (nicht der eigenen Firma), dient der Einschätzung der Unternehmensgröße |
| **Mitarbeiter** | Angenäherte Mitarbeiteranzahl des Geschäftspartners |
| **Km** | Einfache Fahrstrecke in Kilometern; wird als Berechnungsgrundlage für Fahrtkosten in Leistungspositionen verwendet |
| **Innendienst** | T4-Benutzer, der diesen Partner im Innendienst betreut |
| **Außendienst** | T4-Benutzer, der diesen Partner im Außendienst betreut |

---

## 9. Gruppenfelder

Die Gruppenreiter rechts im Formular bestimmen die **Bedeutung der Adresse** für das Unternehmen. Eine Adresse kann gleichzeitig in mehreren Gruppen sein (z. B. Kunde und Lieferant).

> Eine Adresse muss mindestens einer Gruppe zugeordnet sein, um gespeichert werden zu können.

### 9.1 Reiter „Kunde"

| Feld | Beschreibung |
|---|---|
| **Kundengruppe** | Klassifizierung: Endkunde, Großkunde, Händler, Interessent, Key Account. Leerauswahl = kein Kunde. |
| **Vor-Kauf-Status** | Aktuelle Phase vor dem Kauf: Interessent → Angebot → Entscheidungsphase → Stammkunde |
| **Nach-Kauf-Status** | Status nach dem Kauf: Aktiv, Inaktiv, Gesperrt |
| **Zufriedenheit** | Subjektive Kundenbewertung mit Smiley-Darstellung: 😐 indifferent · 😠 unzufrieden · 😊 zufrieden · 😄 Referenz |
| **ABC-Klasse** | Strategische Einstufung: A-Kunde (wichtigste), B-Kunde, C-Kunde |

### 9.2 Reiter „Lieferant"

| Feld | Beschreibung |
|---|---|
| **Lieferantengruppe** | Klassifizierung: Stamm-Lieferant, Gelegenheits-Lieferant, Anfrage-Lieferant. Leerauswahl = kein Lieferant. |
| **Anfragestatus** | Qualifizierungsphase des Lieferanten: Neu → Angefragt → Qualifiziert |
| **Lieferantenstatus** | Aktueller Betriebsstatus: Aktiv, Inaktiv, Gesperrt |
| **Zufriedenheit** | Bewertung der Lieferantenbeziehung (wie beim Kunden, mit Smileys) |

### 9.3 Reiter „Personal"

| Feld | Beschreibung |
|---|---|
| **Personalgruppe** | Klassifizierung: Mitarbeiter, Bewerber, Freie Mitarbeit, Auszubildende |

> Mitarbeiter-Adressen können wie jede andere Adresse mit Vorgängen (Urlaub, Termine, Dokumente) verknüpft werden.

### 9.4 Reiter „Sonstiges"

| Feld | Beschreibung |
|---|---|
| **Sonstige Gruppe** | Für Adressen ohne Kunden-/Lieferanten-/Personalzuordnung: Behörde, Verband, Partnerschaft |
| **Datensatz gesperrt** | Markiert den Datensatz als gesperrt. Gesperrte Datensätze werden in der Liste mit 🔒 angezeigt. |

---

## 10. Untertabellen

Die Untertabellen befinden sich im unteren Bereich des Formulars. Sie zeigen jeweils die zur aktiven Adresse gehörenden Datensätze einer bestimmten Kategorie.

Jede Untertabelle hat eine **„Neu"-Schaltfläche** zum Hinzufügen und ein **🗑️-Symbol** pro Zeile zum Löschen eines Eintrags. Änderungen werden erst nach dem Speichern (Strg+S) dauerhaft gespeichert.

### 10.1 Kommunikation

Erfasst alle Kommunikationswege des Geschäftspartners.

| Feld | Beschreibung |
|---|---|
| **Typ** | Art der Kommunikation: Telefon, Mobil, Fax, E-Mail, Website, Skype, Teams, Daten-Pfad |
| **Nummer / Adresse** | Die eigentliche Telefonnummer, E-Mail-Adresse oder URL |
| **Bemerkung** | Freitext, z. B. „Zentrale", „Privat", „Nur vormittags" |

**Beispiel:**

| Typ | Nummer / Adresse | Bemerkung |
|---|---|---|
| Telefon | +49 228 123456 | Zentrale |
| E-Mail | info@mueller-co.de | Allgemein |
| Teams | info@mueller-co.de | Microsoft Teams |

### 10.2 Ansprechpartner

Personen, die bei diesem Unternehmen als Kontakt zur Verfügung stehen.

| Feld | Beschreibung |
|---|---|
| **Anrede** | Herr, Frau, Divers |
| **Nachname** | Familienname des Ansprechpartners |
| **Vorname** | Vorname |
| **Position** | Funktion/Titel im Unternehmen, z. B. „Geschäftsführer", „Einkauf" |
| **Telefon** | Direkte Durchwahl |
| **E-Mail** | Direkte E-Mail-Adresse |

### 10.3 Bankkonten

Bankverbindungen des Geschäftspartners (für Zahlungsverkehr).

| Feld | Beschreibung |
|---|---|
| **Bank** | Name des Kreditinstituts |
| **IBAN** | Internationale Kontonummer, z. B. `DE89 3704 0044 0532 0130 00` |
| **BIC** | Bank Identifier Code (Swift-Code), z. B. `DEUTDEDB` |
| **Kontoinhaber** | Name des Kontoinhabers (kann vom Adressnamen abweichen) |

### 10.4 Konditionen

Zahlungsbedingungen für Kauf- oder Verkaufsvorgänge.

| Feld | Beschreibung |
|---|---|
| **Typ** | VK-Kondition (Verkauf), EK-Kondition (Einkauf) oder Standard |
| **Ziel (Tage)** | Zahlungsziel in Tagen (z. B. `30` = Zahlung innerhalb 30 Tagen) |
| **Skonto %** | Skontoabzug bei frühzeitiger Zahlung (z. B. `2` = 2 %) |
| **Skonto-Tage** | Anzahl Tage, innerhalb derer Skonto gewährt wird (z. B. `10`) |
| **Währung** | EUR, USD, GBP, CHF |

**Beispiel:** `VK-Kondition · 30 Tage · 2 % Skonto bei 10 Tagen · EUR`
Bedeutet: Zahlbar innerhalb 30 Tagen, bei Zahlung innerhalb 10 Tagen 2 % Abzug.

### 10.5 Suchbegriffe

Freie Schlüsselwörter, über die diese Adresse in der Suche gefunden werden kann.

- Geben Sie einen Begriff im Eingabefeld ein und drücken Sie **Enter** oder klicken Sie **Hinzufügen**.
- Suchbegriffe werden als Tags dargestellt und können einzeln über das **×** entfernt werden.
- Die Adress-Nr. wird automatisch als Suchbegriff geführt.

**Beispiel:** `Müller` · `GmbH` · `Bonn` · `Großkunde` · `100001`

### 10.6 Beziehungen

Verknüpfungen dieser Adresse mit anderen Adressen im System.

| Feld | Beschreibung |
|---|---|
| **Beziehungstyp** | Art der Beziehung: Konzernmutter, Tochtergesellschaft, Partner, Konditionsherkunft, Lieferadresse, Rechnungsadresse |
| **Adresse** | Name oder Nummer der verknüpften Adresse |
| **Betreff / Bemerkung** | Freitext zur Erläuterung der Beziehung |

> **Hinweis Konditionsherkunft:** Ist eine Beziehung vom Typ „Konditionsherkunft" eingetragen, kann bei der Vorgangserfassung zwischen den Konditionen der eigenen Adresse und der Herkunftsadresse gewählt werden.

### 10.7 Infomerkmale

Individuelle Schlüssel-Wert-Paare für Informationen, die in keine andere Kategorie passen.

| Feld | Beschreibung |
|---|---|
| **Merkmal** | Name des Merkmals, z. B. „Messeteilnahme", „Zertifizierung" |
| **Wert** | Wert des Merkmals, z. B. „ja", „ISO 9001" |
| **Bemerkung** | Zusätzliche Erläuterung, z. B. „Hannover Messe 2025" |

---

## 11. Suche und Filter

### Volltextsuche

Das Suchfeld in der Seitenleiste filtert die Adressliste in Echtzeit. Gesucht wird in:
- Name der Adresse
- Adress-Nummer
- Ort und PLZ
- allen eingetragenen Suchbegriffen

Groß- und Kleinschreibung wird dabei nicht unterschieden.

**Tipp:** Mit `Strg+F` springen Sie direkt in das Suchfeld.

### Gruppenfilter

Die Schaltflächen **Alle / Kunden / Lief. / Perso** schränken die Anzeige auf Adressen mit der jeweiligen Gruppenzuordnung ein. Suche und Gruppenfilter wirken kombiniert.

**Beispiel:** Filter „Kunden" + Suchbegriff „Berlin" → zeigt nur Kunden aus Berlin.

---

## 12. Lesezeichen

Adressen, die Sie besonders häufig benötigen, können als Lesezeichen (Favoriten) markiert werden.

**Lesezeichen setzen:** Klicken Sie auf **⭐ Lesezeichen** in der Toolbar, während die gewünschte Adresse angezeigt wird. Das Symbol wechselt zu einem ausgefüllten goldenen Stern.

**Lesezeichen entfernen:** Erneuter Klick auf die Schaltfläche.

Markierte Adressen sind in der Adressliste mit einem goldenen ⭐ vor dem Namen gekennzeichnet.

---

## 13. Datenspeicherung

Die Anwendung speichert alle Daten im **localStorage** des Browsers. Das bedeutet:

| Eigenschaft | Details |
|---|---|
| **Speicherort** | Im Browser, lokal auf diesem Gerät |
| **Automatisch?** | Nein – manuell über **Speichern** (Strg+S) |
| **Verlust bei Browser-Schließen?** | Nein – Daten bleiben dauerhaft erhalten |
| **Sichtbar in anderen Browsern?** | Nein – nur im selben Browser auf demselben Gerät |
| **Sichtbar im privaten Modus?** | Nein – im privaten/Inkognito-Modus gehen Daten verloren |

### Speichern nicht vergessen!

Ungespeicherte Änderungen sind an einem **gelben Punkt** in der Statusleiste erkennbar. Verlassen Sie einen Datensatz ohne zu speichern, fragt die Anwendung nach, ob die Änderungen verworfen werden sollen.

### Datensicherung

Da die Daten nur im Browser gespeichert sind, empfiehlt sich eine regelmäßige Sicherung:

1. Drücken Sie `F12` im Browser (Entwicklertools öffnen)
2. Wechseln Sie zu **Application → Local Storage**
3. Kopieren Sie den Wert von `t4_adressen_v1`
4. Speichern Sie diesen Text als Backup-Datei

---

## 14. Tastaturkürzel

| Kürzel | Funktion |
|---|---|
| `Strg+S` | Aktuellen Datensatz speichern |
| `Strg+N` | Neuen Datensatz anlegen |
| `Strg+F` | Fokus in die Suche setzen |
| `Enter` | Im Suchbegriff-Feld: Suchbegriff hinzufügen |

---

## 15. Häufige Fragen (FAQ)

**F: Ich habe versehentlich einen Datensatz gelöscht – kann ich ihn wiederherstellen?**
A: Nein, gelöschte Datensätze können nicht automatisch wiederhergestellt werden. Erstellen Sie regelmäßig Backups (siehe Abschnitt 13).

---

**F: Kann ich die Anwendung auf mehreren Geräten gleichzeitig nutzen?**
A: Die Anwendung speichert Daten lokal im Browser und hat keine Synchronisierung. Auf jedem Gerät gibt es eine eigene, unabhängige Datenbasis.

---

**F: Wie kann ich alle Adressen exportieren?**
A: Die aktuelle Version unterstützt keinen direkten Export. Die Rohdaten können über die Browser-Entwicklertools (F12 → Application → Local Storage → `t4_adressen_v1`) als JSON-Text kopiert werden.

---

**F: Eine Adresse ist als gesperrt markiert – was bedeutet das?**
A: Gesperrte Datensätze sind mit einem roten 🔒 in der Liste gekennzeichnet. Die Sperre ist ein informatives Merkmal und schränkt die Bearbeitung in dieser Web-App nicht ein. In einem vollständigen ERP-System würden gesperrte Adressen bei der Anlage neuer Vorgänge als Warnung angezeigt.

---

**F: Warum zeigt die Anwendung „Alle Änderungen gespeichert", obwohl ich noch nichts gespeichert habe?**
A: Beim Start der Anwendung werden entweder die zuletzt gespeicherten Daten aus dem Browser-Speicher geladen oder die Demo-Daten. In beiden Fällen gibt es initial keine ungespeicherten Änderungen.

---

**F: Kann eine Adresse gleichzeitig Kunde und Lieferant sein?**
A: Ja. Füllen Sie sowohl die **Kundengruppe** im Reiter „Kunde" als auch die **Lieferantengruppe** im Reiter „Lieferant" aus. In der Adressliste werden dann beide Badges (**K** und **L**) angezeigt.

---

*© 2026 – Benutzerhandbuch für die MQ6 Adressverwaltung Web-App*
*Erstellt auf Basis des „Themenhandbuch Adressen" der TETRA GmbH, Wachtberg*
