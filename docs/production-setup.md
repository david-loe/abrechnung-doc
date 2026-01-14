## Produktionsmodus aktivieren

Setze die Umgebungsvariable:

```sh
NODE_ENV=production
```

## Docker Compose

Binde die folgende `docker-compose`-Datei ein:

```yaml
--8<-- "https://raw.githubusercontent.com/david-loe/abrechnung/main/deploy-compose.yml"
```

ℹ️ **Vergiss nicht**, die erforderlichen [Umgebungsvariablen](https://github.com/david-loe/abrechnung/blob/main/.env.example) entweder in der `.env`-Datei oder direkt in der `compose.yml` zu setzen.

## Verbindungseinstellungen vorkonfigurieren

Falls du die Verbindungseinstellungen nicht über den Admin-Link aus dem Backend-Log in der UI konfigurieren möchtest, kannst du diese auch direkt per JS-Datei festlegen.

### ℹ️ Wichtige Hinweise

- Die Konfiguration wird **nur angewendet, wenn noch keine Verbindungseinstellungen in der Datenbank vorhanden sind**.
- Falls bereits Einstellungen gespeichert wurden, musst du den entsprechenden Eintrag in der `connectionsettings`-Collection der Datenbank **löschen**, um ihn zu überschreiben.

### Konfigurationsdatei überschreiben

Um eigene Einstellungen zu verwenden, überschreibe die folgende Datei im Backend-Container:

```plaintext
/build/dist/data/connectionSettings.production.js
```

Dies kann über ein Docker-Volume erfolgen:

```yaml
volumes:
  - ./connectionSettings.production.js:/build/dist/data/connectionSettings.production.js
```

### Orientierungshilfen für die Konfiguration

- Beispielkonfiguration: [`connectionSettings.development.ts`](https://github.com/david-loe/abrechnung/blob/main/backend/data/connectionSettings.development.ts)
- Datenbank-Schema: [`ConnectionSettings`](https://github.com/david-loe/abrechnung/blob/main/backend/models/connectionSettings.ts)
