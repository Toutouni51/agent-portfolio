---
name: sponsors-evenement-local
description: "Trouve et qualifie des entreprises locales susceptibles de financer ou sponsoriser un événement sportif associatif : dons en trésorerie (mécénat), paiement de lots de t-shirts contre logo, produits pour ravitaillements et sacs coureurs, lots. Produit un tableau et un CSV importable dans un CRM. À utiliser quand l'utilisateur cherche des sponsors, des mécènes ou des partenaires pour son événement."
---

# Sponsors d'événement local — prospection de financeurs

Tu aides l'organisateur d'un événement sportif associatif à constituer une liste d'entreprises à démarcher. Commence par lui demander le territoire visé, le nombre de participants attendu et ce qu'il peut offrir en contrepartie.

Conséquences pour le ciblage d'une petite première édition :
- Priorité aux PME, commerces et producteurs du territoire, pour qui quelques centaines de participants locaux sont une audience utile. Les grands groupes se démarchent par l'agence ou le magasin local, pas par le siège.
- Proposer des paliers de partenariat accessibles plutôt qu'un gros sponsor unique.
- Les aides publiques réservées aux événements de niveau régional ou national risquent de ne pas s'appliquer : le signaler plutôt que de les présenter comme acquises.

## Ce que l'on cherche

| Code | Apport | Cibles naturelles |
|---|---|---|
| `TRESO` | Don en trésorerie (mécénat ou sponsoring) | Banques, mutuelles, grande distribution locale, PME installées |
| `MERCH` | Paiement d'un lot de t-shirts contre logo | Marques textiles, concessions, commerces de sport, artisans |
| `PRODUITS` | Produits pour ravitaillements, village d'arrivée, sac coureur | Producteurs et artisans de l'alimentation |
| `LOTS` | Lots pour les podiums ou la tombola | Hôtels, restaurants, parcs de loisirs, boutiques |

## Critères de qualification

Note chaque entreprise sur 10 en additionnant :

- **Ancrage** (0–3) : 3 = siège sur le territoire de l'événement ; 2 = dans le département ; 1 = dans la région ; 0 = établissement local d'un groupe national.
- **Lien avec le territoire** (0–3) : 3 = produit identitaire ; 2 = marque qui revendique son ancrage local ; 1 = commerce local ; 0 = aucun.
- **Habitude du sport** (0–3) : 3 = sponsor avéré d'une course de la région ; 2 = sponsor d'un autre événement sportif ; 1 = soutient des associations locales ; 0 = rien trouvé.
- **Accessibilité** (0–1) : 1 = on a trouvé une page partenariats, un formulaire, un email générique ou un nom de responsable.

Priorité : A (8–10), B (5–7), C (≤ 4). Ne garde les C que si l'utilisateur demande de l'exhaustivité.

## Méthode

### 1. Charger ce qui existe déjà
Écarte les entreprises déjà présentes dans les fichiers ou l'export CRM fournis par l'utilisateur (comparaison sans accents ni casse).

### 2. Trouver les candidats, dans cet ordre
1. **Pages partenaires des courses et événements du secteur** : c'est la preuve la plus forte, car l'entreprise sponsorise déjà.
2. **Réseaux d'entreprises** : labels régionaux, clubs d'entreprises, chambres de commerce.
3. **Producteurs locaux** : pages « visites d'entreprises » et « dégustation » des offices de tourisme.
4. **Presse locale** : `"[entreprise]" partenaire course OR sponsor OR mécène`.

Lance les recherches en parallèle par lots.

### 3. Qualifier chaque candidat
Pour chaque entreprise retenue, note :
- ville du siège ou de l'établissement local ;
- **preuve** de soutien sportif (événement, année, URL) ;
- apport le plus plausible (`TRESO`, `MERCH`, `PRODUITS`, `LOTS`) ;
- **angle d'accroche** en une phrase ;
- **contact** : page partenariat, formulaire, email générique publié ou responsable communication/marketing.

**N'invente jamais d'email ni de nom.** Si rien n'est trouvé, écris « site : [url] » ou « formulaire : [url] ». Un email déduit d'un format doit être marqué « (supposé) ».

### 4. Livrer

**a) Un tableau récapitulatif**, trié par priorité puis score :

| Prio | Entreprise | Ville | Apport | Preuve sport | Accroche | Contact |

**b) Un CSV** encodé en UTF-8 avec BOM, séparateur virgule, avec ces en-têtes :

```
Contact,Coordonnées,Fonction,Intérêt /Apport potentiel,État du processus,Commentaire
```

- `Contact` : nom de l'entreprise, toujours avec la même orthographe pour le dédoublonnage.
- `Coordonnées` : email, téléphone ou URL du formulaire.
- `Fonction` : personne ou service à viser.
- `Intérêt /Apport potentiel` : `[Prio A|B|C – score/10] APPORT1 + APPORT2 – ville`.
- `État du processus` : `À contacter`.
- `Commentaire` : preuve sportive avec URL et angle d'accroche.

Mets les champs entre guillemets dès qu'ils contiennent une virgule, un guillemet ou un saut de ligne.

## Arguments à rappeler quand c'est utile

- **Mécénat (France)** : si l'association est d'intérêt général, un don d'entreprise peut ouvrir droit à une réduction d'impôt. Les contreparties doivent rester modestes ; au-delà, c'est du **sponsoring**. Conseiller de vérifier les conditions en vigueur et de demander un rescrit avant d'émettre des reçus fiscaux.
- **Mécénat en nature** : un producteur qui fournit ses produits peut aussi être concerné.
- **T-shirts** : proposer un lot chiffré à partir d'un vrai devis facilite la décision. Plusieurs sponsors au logo partagé sont souvent plus faciles à trouver qu'un seul.
