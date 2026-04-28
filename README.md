# 🐘 Screen-Ellophant | Deployment & Release Guideline

> **Wichtiger Hinweis:** Diese Guideline definiert den verbindlichen Workflow für die Bereitstellung neuer Softwareversionen von **Screen-Ellophant**. Die strikte Einhaltung der Reihenfolge stellt die Integrität des Auto-Updaters und die Konsistenz der Repository-Historie sicher.

---

## 📋 Release-Protokoll (Schritt-für-Schritt)

### 1. Versions-Definition
* Festlegung der neuen Versionsnummer nach dem Semantic Versioning Muster: `x.x.x`

### 2. Metadaten-Synchronisation
* Manuelles Ersetzen der Versionsnummer in den folgenden Systemdateien:
    * `Updater.json` (**3x**)
    * `package.json` (**1x**)
    * `package-lock.json` (**1x**)
    * `tauri.conf.json` (**1x**)
    * `StartingWindow/index.html` (**1x**)

### 3. Build-Push
* Übertragen der Änderungen in das Repository mit folgendem Befehl:
    ```bash
    git push "build vx.x.x"
    ```
    *(Beispiel: `git push "build v1.0.2"`)*

### 4. Git-Tagging
* Erstellung und `push` eines neuen Tags: `"vx.x.x"`
    *(Beispiel: `v1.0.2` // Anmerkung ist optional)*

### 5. Repository-Hygiene
* Eventuelles Löschen alter Tags im **lokalen Repository** sowie im **Remote** (GitHub).

### 6. CI/CD Monitoring
* Warten in GitHub auf den **Actions-Build** mit der integrierten `public signatur`.
    * *Dauer: ca. 5-10 Minuten.*

### 7. Signatur-Dekodierung
* Die generierte Signatur liegt im **Base64-Format** vor und muss dekodiert werden:
    * 🔗 **Tool:** [https://www.base64decode.org/](https://www.base64decode.org/)

### 8. Signatur-Extraktion
* Aus dem generierten Klartext muss die finale Signatur ausgeschnitten werden.
    * *Schnittbereich:* `"trusted comment…"`

### 9. Updater-Finalisierung
* Einfügen der extrahierten `pub-Signatur` in die Datei `Updater.json`.

### 10. Finaler Release-Push
* Abschluss des Updates durch den Release-Befehl:
    ```bash
    git push "release update vx.x.x"
    ```
    *(Beispiel: `git push "release update v1.0.2"`)*

### 11. Deployment-Wartezeit
* Warten auf den **GitHub-Pages Build**.
    * *Dauer: ca. 1 Minute.*

### 12. Update-Verfügbarkeit
* Nach Abschluss des Builds ist das neue Update erfolgreich bereitgestellt und für alle Nutzer verfügbar.

---

**Screen-Ellophant** *Professional Presentation & Stage Technology Software* © 2026 Release Engineering Workflow
