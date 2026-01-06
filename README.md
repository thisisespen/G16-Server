
# G16 Server

Dette repositoryet er **autorativ kilde** for arkitektur, krav og konfigurasjon
for G16 Server.

Repoet inneholder:
- 📘 Systeminstruks (policy, standarder og endringskontroll)
- 🐳 Docker Compose-filer per applikasjon
- 📋 Operative sjekklister og vedlegg

Målet er:
- forutsigbar drift
- reproduserbar installasjon
- minimal teknisk gjeld
- tydelig eierskap og endringskontroll

---

## Struktur

```text
docs/
  G16_Server_Systeminstruks.md   # FASIT – styrende dokument
compose/
  <app-navn>/
    docker-compose.yml           # autorativ implementasjon
    .env.example                 # uten secrets
