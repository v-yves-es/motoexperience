# GitHub Pages Deployment Guide

## Stap 1: Repository Setup

1. **Initialiseer Git repository** (als nog niet gedaan):
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   ```

2. **Maak repository op GitHub**:
   - Ga naar https://github.com/new
   - Naam: `motoexperience` (of een andere naam)
   - Maak repository **public** (GitHub Pages werkt gratis alleen voor public repos)
   - Maak GEEN README, .gitignore of license aan (je hebt die al)

3. **Push naar GitHub**:
   ```bash
   git remote add origin https://github.com/JOUW-USERNAME/motoexperience.git
   git branch -M main
   git push -u origin main
   ```

## Stap 2: GitHub Pages Activeren

1. Ga naar je repository op GitHub
2. Klik op **Settings** (tandwiel icoon)
3. Scroll naar beneden naar **Pages** (in het linker menu)
4. Onder **Source**, selecteer:
   - Branch: `main`
   - Folder: `/ (root)`
5. Klik **Save**
6. Na een paar minuten is je site live op: `https://JOUW-USERNAME.github.io/motoexperience/`

## Stap 3: Custom Domain Instellen

### A. In GitHub:

1. Ga naar **Settings** → **Pages**
2. Onder **Custom domain**, vul in: `www.motoexperience.be`
3. Klik **Save**
4. Wacht tot de DNS check slaagt
5. Vink aan: **Enforce HTTPS** (voor SSL/beveiligde verbinding)

### B. Bij je domeinprovider (bv. Combell, TransIP, etc.):

Je hebt 2 opties:

#### Optie 1: WWW subdomain (aanbevolen)
Voeg deze DNS records toe:

```
Type: CNAME
Name: www
Value: JOUW-USERNAME.github.io
TTL: 3600
```

```
Type: A
Name: @
Value: 185.199.108.153
```

```
Type: A
Name: @
Value: 185.199.109.153
```

```
Type: A
Name: @
Value: 185.199.110.153
```

```
Type: A
Name: @
Value: 185.199.111.153
```

#### Optie 2: Apex domain (zonder www)
Als je `motoexperience.be` wilt (zonder www):

```
Type: A
Name: @
Value: 185.199.108.153
```

```
Type: A
Name: @
Value: 185.199.109.153
```

```
Type: A
Name: @
Value: 185.199.110.153
```

```
Type: A
Name: @
Value: 185.199.111.153
```

### C. CNAME bestand
GitHub maakt automatisch een `CNAME` file aan in je repo. Als dat niet gebeurt:

```bash
echo "www.motoexperience.be" > CNAME
git add CNAME
git commit -m "Add custom domain"
git push
```

## Stap 4: Wachten op DNS Propagatie

- DNS wijzigingen kunnen **15 minuten tot 48 uur** duren
- Check status op: https://www.whatsmydns.net/
- Vul je domein in en kijk of de A records wereldwijd zichtbaar zijn

## Stap 5: HTTPS/SSL Forceren

Na DNS propagatie (meestal binnen een uur):
1. Ga naar **Settings** → **Pages**
2. Vink aan: **Enforce HTTPS**
3. Klaar! Je site is nu beveiligd met gratis SSL van GitHub

## Updates Pushen

Wanneer je wijzigingen maakt:

```bash
git add .
git commit -m "Beschrijving van wijziging"
git push
```

GitHub Pages update automatisch binnen 1-2 minuten.

## Voordelen

✅ **Gratis hosting** - Geen kosten
✅ **Gratis SSL** - Automatische HTTPS
✅ **CDN** - Snel over heel de wereld
✅ **Geen server onderhoud** - GitHub regelt alles
✅ **Eigen domein** - Niemand ziet dat het op GitHub staat
✅ **Uptime** - 99.9% beschikbaarheid

## Belangrijke Opmerkingen

⚠️ **Repository moet public zijn** voor gratis GitHub Pages
⚠️ **Geen server-side code** - Alleen statische HTML/CSS/JS (wat je hebt is perfect)
⚠️ **Geen PHP/databases** - Gebruik externe services als je die nodig hebt
⚠️ **100 GB bandwidth/maand** - Ruim voldoende voor deze site

## Troubleshooting

### Site niet zichtbaar na 10 minuten?
- Check of GitHub Pages is ingeschakeld in Settings
- Controleer of `index.html` in de root staat (✓ bij jou)
- Kijk naar de Actions tab voor build errors

### Custom domain werkt niet?
- Wacht langer (DNS kan 48u duren)
- Check DNS records bij je provider
- Zorg dat CNAME file `www.motoexperience.be` bevat (of je gekozen domein)

### HTTPS werkt niet?
- Wacht tot DNS volledig is gepropageerd
- Disable en enable "Enforce HTTPS" opnieuw
- Kan tot 24u duren na DNS wijziging

## Support

GitHub Pages Documentatie: https://docs.github.com/en/pages
