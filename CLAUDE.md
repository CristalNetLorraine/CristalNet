# Cristal Net Lorraine — Site vitrine

Site one-page pour Cristal Net Lorraine, prestataire de nettoyage de vitres et panneaux solaires dans les Vosges (88) et toute la Lorraine. Lancé en 2026.

## Stack

- HTML/CSS/JS pur — aucun framework, aucun bundler, aucune dépendance npm
- Polices auto-hébergées : Big Shoulders (titres) + Nunito (corps) dans `fonts/`
- EmailJS (CDN) pour l'envoi des demandes de devis par email

## Structure

```
index.html              Page unique — tout le HTML, CSS et JS est inline ou chargé depuis
assets/images/          Logos (PNG)
fonts/
  Big_Shoulders/        Variable font — titres
  Nunito/               Variable font — corps de texte
js/
  config.js             GITIGNORÉE — credentials EmailJS (à créer depuis config.example.js)
  config.example.js     Template de configuration à copier
.gitignore
CLAUDE.md
```

## Configuration email (formulaire de devis)

Les demandes de devis passent par **EmailJS**. Le destinataire est configuré dans le template EmailJS — l'adresse email n'apparaît jamais dans le code source.

### Mise en place (avant mise en ligne)

1. Créer un compte sur [emailjs.com](https://www.emailjs.com)
2. Créer un **Email Service** (Gmail, SMTP, etc.)
3. Créer un **Email Template** avec les variables suivantes :
   - `{{from_name}}` — prénom + nom du demandeur
   - `{{from_email}}` — email du demandeur
   - `{{phone}}` — téléphone
   - `{{service}}` — service souhaité
   - `{{message}}` — message libre
4. Copier `js/config.example.js` → `js/config.js`
5. Renseigner les trois clés dans `js/config.js` :
   - `emailjs_public_key` — Account > API Keys
   - `emailjs_service_id` — Email Services > votre service
   - `emailjs_template_id` — Email Templates > votre template

> `js/config.js` est gitignorée. Ne jamais committer ce fichier.

## Développement

Ouvrir `index.html` directement dans un navigateur. Aucun serveur local requis (sauf pour tester l'envoi email — EmailJS fonctionne depuis `file://`).

## À compléter avant mise en ligne

Chercher `À compléter` dans `index.html` pour trouver tous les champs :

- Numéro de téléphone (section Contact + Footer)
- Adresse email affichée (section Contact + Footer + Mentions légales)
- Raison sociale, forme juridique, SIRET, adresse (Mentions légales)
- Directeur de la publication (Mentions légales)
- Hébergeur (Mentions légales)
- Photos réelles (remplacer les images `picsum.photos`)
- Configuration EmailJS (voir ci-dessus)

## Design

| Token CSS      | Valeur    | Usage                    |
|----------------|-----------|--------------------------|
| `--navy`       | `#12264F` | Titres, boutons primaires |
| `--blue`       | `#1A8BC2` | Accents, icônes, liens    |
| `--blue-lt`    | `#5DB8E0` | Accents clairs            |
| `--ice`        | `#E8F5FB` | Fonds de cartes           |
| `--canvas`     | `#FBFBFA` | Fond de page              |

Polices : Big Shoulders (800) pour les titres, Nunito (400–700) pour le corps.
