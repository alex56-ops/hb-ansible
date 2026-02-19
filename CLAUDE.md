# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Projektbeschreibung

Ansible-Projekt zur Serveradministration und Service-Bereitstellung.

## Befehle

```bash
# Syntax-Check eines Playbooks
ansible-playbook playbooks/<name>.yml --syntax-check

# Playbook im Dry-Run ausführen
ansible-playbook playbooks/<name>.yml --check --diff

# Playbook ausführen
ansible-playbook playbooks/<name>.yml

# Einzelne Rolle testen (mit Tag)
ansible-playbook playbooks/<name>.yml --tags <rollenname>

# Vault-Datei bearbeiten
ansible-vault edit <datei>

# Lint-Prüfung
ansible-lint
```

## Projektstruktur

Das Projekt folgt der Standard-Ansible-Verzeichnisstruktur:

- `inventories/` — Inventory-Dateien (Hosts, Gruppen)
- `playbooks/` — Playbooks
- `roles/` — Rollen mit Standardstruktur (tasks, handlers, templates, defaults, vars, files)
- `group_vars/` — Gruppenvariablen (ggf. Vault-verschlüsselt)
- `host_vars/` — Hostvariablen (ggf. Vault-verschlüsselt)

## Konventionen

- **Secrets**: Gehören ausschließlich in Ansible-Vault-verschlüsselte Dateien. Niemals Klartext-Secrets in Rollen, Playbooks oder Templates. Platzhalter einfügen — Verschlüsselung erfolgt manuell.
- **Neue Services**: Vor dem Erstellen einer neuen Rolle mindestens zwei bestehende, vergleichbare Rollen analysieren und deren Struktur und Muster übernehmen.
- **Strukturtreue**: Bestehende Verzeichnis- und Dateistruktur strikt einhalten. Keine neuen Muster einführen, die von bestehenden Rollen abweichen.
- **Commits**: Niemals eigenständig Commits erstellen. Commits erfolgen ausschließlich über den `/ship` Skill.
- **Sprache**: Kommunikation erfolgt auf Deutsch.
