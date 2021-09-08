# SWUPATE

- [Wichtige Hinweise](https://docs.shopware.com/de/shopware-5-de/update-guides/update-guide-shopware-56?category=shopware-5-de/update-guides#verwaiste-eintraege-in-s-order-details)
- [Update Vorgang](https://docs.shopware.com/de/shopware-5-de/update-guides/shopware-aktualisieren-updaten?category=shopware-5-de/update-guides)

## Ablauf
1. Backups Erstellen
```
Backup des LIVE Systems machen [custom, engine/Shopware/Plugins, themes]
Backup des bearbeiteten Update Systems (am besten nochmal lokal) abspeichern [custom, engine/Shopware/Plugins, themes]
Backup des bearbeiteten Update Systems in einem Unterverzeichnis des Update Servers sichern
```
2. Update-System platt machen und neu aufsetzen (Stand vom Live-System)
```
auf IPLIVE copy-live-server.sh ausführen
auf IPUPDATE copy-update-server.sh ausführen
```
3. Erneuten Dump ziehen / importieren und geänderten Dateien vom Live-Server übertragen
```
auf IPLIVE copy-live-server.sh ausführen
auf IPUPDATE copy-update-server.sh ausführen
```
4. Cache leeren
5. Host-Eintrag/Einträge setzen:
```
IP address.de
IP www.address.de
```
6. Query ausführen
```
DELETE from s_order_details  WHERE orderID Not IN (Select id from s_order) (5.6.10)
```
8. Update-Paket hochladen und Update durchführen
9. alle Plugins über den Plugin Manager auf die jeweils neuste Version UPDATEN & NICHT NEU INSTALLIEREN!
10. Folgende Ordner vom vorherigen Update-System (am besten extra lokal sichern) mit dem neu aktualisierten Update-Server mergen:
```
custom/plugins
engine/Shopware/Plugins
themes/Frontend/<CUSTOM THEME>
themes/Frontend/<HELPER THEME> (Falls vorhanden!)
```
