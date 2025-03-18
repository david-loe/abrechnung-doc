## Docker Compose

```yaml
--8<-- "https://raw.githubusercontent.com/david-loe/abrechnung/main/deploy-compose.yml"
```

ℹ️ Vergiss nicht die [Umgebungsvariablen](https://github.com/david-loe/abrechnung/blob/main/.env.example) entweder in der `.env` Datei oder direkt in der `compose.yml` zu setzen.

## Verbindungseinstellungen Vorkonfigurieren

Wenn du die Einstellungen nicht über den Admin Link aus dem Backend-Log in der UI einstellen willst, kannst du diese auch per JSON Konfiguration setzten.

> ℹ️ Die JSON Konfiguration wird nur dann gesetzt wenn noch keine Einstellung in der Datenbank vorliegt. Um bestehende Einstellungen zu überschrieben musst du den Eintrag in der `connectionsettings` collection aus der Datenbank löschen.

Für die Konfiguration kannst du dich an der [`connectionSettings.development.json`](https://github.com/david-loe/abrechnung/blob/main/backend/data/connectionSettings.development.json) und dem Model Schema [`ConnectionSettings`](https://github.com/david-loe/abrechnung/blob/main/backend/models/connectionSettings.ts) orientiren.
