# Villa Verdun — Cassis

Site de présentation et brochure premium du bien, sur le modèle de
[chaletfontromeu](https://github.com/lacremetech-cloud/chaletfontromeu).

## Structure

```
index.html               landing
styles.css               feuille de style (polices auto-hébergées incluses)
main.js                  navigation, révélations, modale, galerie plein écran
brochure/index.html      brochure A4 — 16 pages, autonome, imprimable en PDF
assets/images/           15 photographies du bien
assets/fonts/            Cormorant Garamond & Jost (OFL 1.1), 20 fichiers woff2
assets/brand/            logo Prodigio (source, mot-symbole blanc, mot-symbole encre)
direction-artistique/    archive : comparatif des trois directions proposées
```

Site statique : aucun build, aucune dépendance. Déploiement direct sur Vercel.

## Direction artistique

Direction « Calanque », retenue parmi trois propositions. La palette est prélevée
sur les photographies du bien : le bleu `#5C7488` est celui des meubles de cuisine
et des volets. Typographie Cormorant Garamond (titres) et Jost (textes).

Les polices sont servies depuis le dépôt — aucune requête vers Google Fonts,
donc aucun transfert de données vers un tiers.

## Fond animé du hero

La photo aérienne reste la couche de base : elle s'affiche immédiatement, sert
d'affiche pendant le chargement et de solution de repli. La vidéo se fond
par-dessus une fois qu'elle joue réellement.

Elle n'est pas chargée du tout sur mobile (moins de 761 px), quand l'utilisateur
a désactivé les animations, ni sur connexion lente ou en mode données réduites.
Elle se met en pause dès que le hero sort du champ.

Deux sources possibles, réglées en tête de `main.js` :

| Constante | Rôle |
|---|---|
| `HERO_VIDEO_MP4` | Fichier servi depuis le dépôt. **À privilégier** : aucun tiers, aucun logo, cadrage et boucle maîtrisés. Vide pour l'instant. |
| `HERO_VIDEO_ID` | Vidéo YouTube, intégrée via l'API officielle en domaine sans cookie. Actuellement `UE3kntZkW8o`, à partir de 40 s. |

Renseigner `HERO_VIDEO_MP4` suffit à basculer sur le fichier local : il prend
automatiquement le pas sur YouTube.

**Droits.** La vidéo `UE3kntZkW8o` — *CASSIS 🇫🇷 Drone Aerial 4K* — est l'œuvre de
**Polychronis Film**. L'intégration YouTube est le seul usage légitime d'une vidéo
tierce : elle reste servie par YouTube, l'auteur conserve attribution et
monétisation. Un téléchargement suivi d'un ré-hébergement sur le site serait une
contrefaçon. Pour un usage pleinement maîtrisé, il faut soit l'accord écrit de
l'auteur, soit des images propres au bien.

## À renseigner avant mise en ligne

| Élément | Emplacement |
|---|---|
| Pixel Meta | `index.html`, commentaire `TODO Meta Pixel` |
| Tunnel Systeme.io | `main.js`, constante `FORM_SCRIPT_URL` |
| E-mail de contact | `main.js`, constante `CONTACT_EMAIL` |
| Lien WhatsApp | `main.js`, constante `CONTACT_WHATSAPP` |
| Coordonnées Prodigio | `brochure/index.html`, page 16 |
| Mentions légales, confidentialité | pied de page, liens `#` |

## Points à trancher

**Adresse.** L'état des risques et pollutions du 26/06/2026 (réf. 3739891) porte sur
le **17 avenue de Verdun**, parcelle cadastrée **CL 58**. La description transmise
indique **20 boulevard Jean Jaurès**. En attendant l'arbitrage, aucune adresse précise
n'est publiée — ce qui correspond de toute façon à l'usage pour une diffusion
confidentielle.

**Descriptions divergentes.** Deux descriptions du bien ont été fournies. La plus
récente fait foi dans les textes actuels :

| | Première version | Version retenue |
|---|---|---|
| Surface | 160 m² | **170 m²** |
| Chambres | 4 suites parentales | **4 chambres avec salle d'eau, dont 1 suite de plain-pied** |
| Stationnement | places privatives | **1 place** |

Repris de la première version faute de contradiction : parcelle de 400 m²,
cave de 6 m², taxe foncière de 1 000 €, piscine en béton armé, garanties.

## Photographies manquantes

Aucune vue de la cuisine d'été ni de la cave. Toutes les vues intérieures montrent
la maison vide.

## Logo

Le PNG fourni présente un défaut : les lettres de la baseline se chevauchent
(« IMMMOBILIER D'EXCEPTTIOON »). Seul le mot-symbole est donc utilisé ; la baseline
est composée dans la typographie du site.
