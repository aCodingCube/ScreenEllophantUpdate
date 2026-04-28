# 🐘 Screen-Ellophant | Release & Update Guideline

Dieses Dokument beschreibt den verbindlichen Workflow für die Entwicklung und Bereitstellung von Updates für **Screen-Ellophant**. Alle Schritte müssen chronologisch befolgt werden, um die Integrität der Software und des Auto-Updaters zu gewährleisten.

---

## 🛠 Deployment-Workflow (12 Schritte)

### 1. Versions-Definition
Festlegung der neuen Versionsnummer nach dem Semantic Versioning Muster: `x.x.x` (Major.Minor.Patch).

### 2. Metadaten-Synchronisation
Die neue Versionsnummer muss in den folgenden Dateien manuell ersetzt werden:
* **Updater.json** (3x)
* **package.json** (1x)
* **package-lock.json** (1x)
* **tauri.conf.json** (1x)
* **StartingWindow/index.html** (1x)

### 3. Build-Commit & Push
Übertragen der Änderungen in das Repository mit dem Build-Identifier:
```bash
git push "build vx.x.x"

Beispiel: git push "build v1.0.2"
4. Tagging

Erstellung eines neuen Git-Tags:
Bash

git tag vx.x.x

Beispiel: vx.x.x (Anmerkung ist optional).
5. Repository-Hygiene

Gegebenenfalls Löschen alter Tags sowohl im lokalen Repository als auch im Remote (GitHub), um Konsistenz zu wahren.
6. GitHub Actions Build

Warten auf den Abschluss des automatischen Builds in GitHub. Dieser Prozess generiert die notwendige pub-Signatur.

    Dauer: ca. 5–10 Minuten.

7. Signatur-Dekodierung

Die generierte Signatur liegt im Base64-Format vor. Diese muss über folgende Plattform dekodiert werden:

    🔗 https://www.base64decode.org/

8. Signatur-Extraktion

Nach der Dekodierung muss die finale Signatur aus dem Klartext ausgeschnitten werden.

    Identifier: Suche nach dem Block "trusted comment…".

9. Updater-Finalisierung

Einfügen der extrahierten pub-Signatur in die Datei:

    Updater.json

10. Finaler Release-Push

Abschluss des Update-Vorgangs durch den Release-Commit:
Bash

git push "release update vx.x.x"

Beispiel: git push "release update v1.0.2"
11. GitHub Pages Build

Warten auf den Build der GitHub Pages Seite.

    Dauer: ca. 1 Minute.

12. Update-Verfügbarkeit

Sobald der Pages-Build abgeschlossen ist, steht das neue Update für alle Instanzen von Screen-Ellophant zur Verfügung.

Screen-Ellophant – Professional Presentation & Stage Technology
