#SWUPATE
  - Wichtige Hinweise https://docs.shopware.com/de/shopware-5-de/update-guides/update-guide-shopware-56?category=shopware-5-de/update-guides#verwaiste-eintraege-in-s-order-details
  - Update Vorgang https://docs.shopware.com/de/shopware-5-de/update-guides/shopware-aktualisieren-updaten?category=shopware-5-de/update-guides

##Ablauf
  1. Backups Erstellen
```python
Backup des LIVE Systems machen (DB, Plugins (custom/themes/legacy_plugins), Themes)
Backup des bearbeiteten Update Systems (custom/themes/legacy_plugins) LOKAL abspeichern
Backup des bearbeiteten Update Systems in einem Unterverzeichnis des Update Servers sichern
```
2. Update-System platt machen und neu aufsetzen (Stand vom Live-System)
```python
auf 83.169.37.205 copy-live-server.sh ausführen
auf 46.163.74.20 copy-update-server.sh ausführen
```
3. Erneuten Dump ziehen / importieren und geänderten Dateien vom Live-Server übertragen
```python
auf 83.169.37.205 copy-live-server.sh ausführen
auf 46.163.74.20 copy-update-server.sh ausführen
```
4. Cache leeren
5. Host-Eintrag setzen:
```python
46.163.74.20 snow-how.de
46.163.74.20 www.snow-how.de
```
6. Query ausführen
```python
DELETE from s_order_details  WHERE orderID Not IN (Select id from s_order) (5.6.10)
```
8. Update-Paket (5.6.10) hochladen und Update durchführen
9. alle Plugins über den Plugin Manager auf die jeweils neuste Version UPDATEN & NICHT NEU INSTALLIEREN!
10. Folgende Ordner vom vorherigen Update-System (liegt lokale bei Keanu) mit dem neu aktualisierten Update-Server mergen:
```python
custom
engine/Shopware/Plugins
themes/Frontend/Snow_How
themes/Frontend/SnowHow_Helper_Theme_After_Plugin
```
