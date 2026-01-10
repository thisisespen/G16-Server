# G16 Server

Dette repositoryet inneholder dokumentasjon og konfigurasjon for **G16 Server** –
en selvhostet serverplattform bygget for stabil drift, tydelig eierskap og full
rekonstruerbarhet.

---

## Viktig: Autorativ dokumentasjon

Den **autorative fasiten** for hele systemet er:

**G16 Server – Autoritativ systeminstruks**

Dette dokumentet:
- definerer arkitektur, krav og styrende prinsipper
- fungerer som rekonstruksjonsinstruks fra blank installasjon
- har **forrang** over all annen dokumentasjon i dette repositoryet

Denne README.md-filen er **underordnet**, beskrivende og veiledende.
Den kan ikke overstyre eller endre krav definert i fasit-dokumentet.

---

## Overordnet arkitektur (kort)

G16 Server er bygget som et lagdelt system med tydelig rollefordeling:

- Maskinvare  
- TrueNAS SCALE (plattform, lagring, ZFS, snapshots, replikering)  
- Docker / Docker Compose (applikasjoner og tjenester)  
- Brukertjenester (eksponert kontrollert via ingress)

Arkitekturen er valgt for:
- enkelhet
- kontroll
- gjenopprettbarhet
- minimal teknisk gjeld

Detaljer er definert i den autorative systeminstruksen.

---

## Ingress, DNS og sikkerhet

### Cloudflare

:contentReference[oaicite:0]{index=0} benyttes som:

- autorativ DNS for domenet
- proxy (gul sky) for eksternt eksponerte tjenester
- første sikkerhets- og filtreringslag før trafikk når serveren

Dette inkluderer blant annet:
- skjuling av reell server-IP
- landbasert tilgangskontroll
- blokkering av uønsket trafikk på kanten

Regler, unntak og detaljer er dokumentert i
**G16 Server – Autoritativ systeminstruks**.

### Reverse proxy og autentisering

- Traefik er eneste ingress til applikasjoner
- TLS termineres i Traefik
- Authentik benyttes som sentral tilgangskontroll (portvakt)

README beskriver dette kun på overordnet nivå.
Detaljert konfigurasjon og krav finnes i fasit-dokumentet.

---

## Docker-applikasjoner og dokumentasjon

Hver applikasjon / stack i G16 Server:

- kjøres i Docker Compose
- har egen prosjektmappe
- dokumenteres i egen Markdown-fil sammen med `docker-compose.yml`

Denne applikasjonsdokumentasjonen er et **driftsverktøy** og skal kunne brukes til:
- forståelse av oppsett
- feilsøking
- kontrollert endring
- gjenoppretting etter feil

Struktur, krav og minimumsinnhold er definert i den autorative systeminstruksen.

---

## Endringer og videre arbeid

- Arkitektur og krav endres **kun** ved revisjon av
  **G16 Server – Autoritativ systeminstruks**
- Endringer skal være:
  - eksplisitte
  - dokumenterte
  - sporbare

README oppdateres kun for å reflektere gjeldende praksis,
ikke for å innføre nye krav.

---

## Changelog (README)

Denne changeloggen gjelder **kun README.md**.
Den erstatter ikke endringsloggen i den autorative systeminstruksen.

### 2026.01.10
- Lagt til eksplisitt seksjon om autorativ dokumentasjon
- Presisert rolle og avgrensning for README
- Dokumentert Cloudflare som DNS- og sikkerhetslag på overordnet nivå
- Strukturert README for samsvar med G16-fasiten

---

## Status

Repositoryet er i aktiv bruk og vedlikehold som del av
**G16 Server**-plattformen.
