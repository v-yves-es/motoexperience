# Spam Bescherming voor Contactformulier

## Huidige bescherming (automatisch door Formspree):
✅ Honeypot velden
✅ Rate limiting
✅ Email validatie
✅ Basis spam detectie

## Extra bescherming toevoegen (optioneel):

### Google reCAPTCHA v2 (GRATIS)

**Stap 1: Krijg reCAPTCHA keys**
1. Ga naar: https://www.google.com/recaptcha/admin
2. Registreer nieuwe site
3. Kies "reCAPTCHA v2" → "I'm not a robot" Checkbox
4. Voeg toe: `www.motoexperience.be` en `motoexperience.be`
5. Krijg:
   - Site key (public)
   - Secret key (private)

**Stap 2: Site key in Formspree**
1. Log in op Formspree.io
2. Ga naar je form settings
3. Zoek "reCAPTCHA"
4. Vul je reCAPTCHA site key in
5. Save

**Stap 3: Code toevoegen**
Voeg toe aan contact.html, voor </form>:

```html
<div class="g-recaptcha" data-sitekey="JOUW_SITE_KEY"></div>
```

En in <head>:
```html
<script src="https://www.google.com/recaptcha/api.js" async defer></script>
```

### Honeypot (al actief via Formspree)
Formspree heeft dit al ingebouwd, maar je kan ook zelf:

```html
<!-- Voeg toe in formulier (onzichtbaar voor mensen, maar bots vullen het in) -->
<input type="text" name="_gotcha" style="display:none">
```

## Aanbeveling voor jou:

**Voor nu: NIETS doen** ✅
- Formspree's basis bescherming is **ruim voldoende** voor 99% van de sites
- Monitor eerste weken of je spam krijgt
- Als je spam krijgt → voeg reCAPTCHA toe

**Waarom niet meteen reCAPTCHA?**
- Extra stap voor gebruikers (conversie ↓)
- Google tracking/cookies (privacy)
- Meestal niet nodig voor kleine sites

## Spam monitoring:

**In je mailbox:**
Als je spam krijgt, zie je het in je inbox bij evert@motoexperience.be

**In Formspree dashboard:**
1. Log in op formspree.io
2. Ga naar je form
3. Zie alle submissions
4. Mark as spam → Formspree leert

## Als je toch spam krijgt:

1. **Optie A:** Voeg reCAPTCHA toe (zie boven)
2. **Optie B:** Upgrade naar Formspree Gold ($10/maand) voor Akismet
3. **Optie C:** Gebruik Cloudflare (gratis) voor extra IP filtering

## TL;DR:
🎯 **Nu:** Niets doen - Formspree beschermt je al
🔍 **Monitor:** Eerste maand checken op spam
🛡️ **Als spam:** reCAPTCHA toevoegen (5 min werk)

Voor een lokale motortraining site is spam meestal geen groot probleem!
