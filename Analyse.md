# Synthèse — Uber en Inde en 2024

**Dataset CSV** — 150 000 réservations  
**uniquement sur Delhi-NCR** (PAS national, juste région de la capitale)

⚠️ le CSV permettra de vérifier finement une seule ville-région, pas de valider les tendances nationales.

---

## Constats

### Contexte
- PIB/habitant modeste (~2 711 $(USD) nominal soit 259 521 roupies / an), en 2024 avec un taux ~83 INR/USD = 7.43 USD /jour.  
Mais fort volume de population et de trajets courts, dans un pays où les travaux publics (routes, aéroports) emploient plus de 30 millions de personnes — infrastructure en pleine expansion.
- Encadrement de l'information limité (159e/180 pour la liberté de la presse), donc les chiffres officiels d'Uber sont une source majeure faute d'enquêtes indépendantes disponibles.

### Usage en essor mais fragile
- 9,2 milliards de km parcourus en 2024, réservations plus que doublées vs. années précédentes.
- **Uber Auto** (pousse-pousse) devance **Uber Go** — signe d'un marché tiré par la **micro-mobilité bon marché**, pas par la voiture individuelle classique.
- Sur le CSV Delhi-NCR (150k lignes) : **Auto est bien le véhicule le plus réservé** (37 419), suivi de Go Mini (29 806) et Go Sedan (27 141) — cohérent avec le constat national.

### Un taux d'échec de trajet important
Sur le CSV :
| Statut | Volume | Part |
|---|---|---|
| Completed | 93 000 | 62 % |
| Cancelled by Driver | 27 000 | 18 % |
| No Driver Found | 10 500 | 7 % |
| Cancelled by Customer | 10 500 | 7 % |
| Incomplete | 9 000 | 6 % |

**Près de 38 % des réservations n'aboutissent pas à un trajet complété.** 
==> Problématique Eddy


### Saisonnalité forte, culturelle et non économique
- Pic absolu le 9 octobre lors de Durga Puja (principales fêtes hindouistes, mais surtout à l'est du pays) comprise dans les fêtes Navratri ==> durant neuf nuits et dix jours diverses formes de la Shakti, l'Énergie féminine divine, en 2024 du 9 au 13 octobre  
pic mensuel en décembre.
- Vendredi = jour le plus réservé ; créneau 18h-19h = heure de pointe.
- Vérifier fête de l'Aïd 16/17 juin 2024
- Multiples fêtes religieuses régionales (Holi, Aïd, Rakhi, Ganesh Chaturthi/Onam) suggèrent une **demande fragmentée par communauté et par région**, pas un calendrier national uniforme.

### Concurrence sur le pricing, pas sur le produit
- Uber Flex (tarif choisi par le passager, avec plancher) répond directement au concurrent inDrive, qui autorise une négociation libre jugée risquée pour les chauffeurs.
- La bataille se joue sur la **flexibilité tarifaire perçue comme équitable**, plus que sur la qualité de service.

### Uber Intercity, pari sur un usage hybride
- Lancé fin 2023, jusqu'à 5 jours, réservable 90 jours à l'avance.
- Cible potentiellement floue : tourisme (Agra/Taj Mahal en tête), pèlerinage, visites familiales, ou déplacements professionnels.

---

## Problématique

> **Dans un marché où près de 4 réservations sur 10 échouent (annulation ou trajet incomplet), la croissance d'Uber en Inde repose-t-elle sur un modèle réellement fiable, ou sur un volume brut qui masque une fragilité opérationnelle et une adaptation encore incomplète aux réalités locales ?**

---

## Hypothèses

1. **Fiabilité inégale selon le type de véhicule.**  
Les véhicules "low-cost" (Auto, eBike/Bike) auraient un taux d'annulation par le chauffeur plus élevé que les véhicules premium (Sedan), les chauffeurs préférant refuser les courses peu rentables.

2. **Fiabilité inégale selon la localisation.**  
Certaines zones de prise en charge (Pickup Location) concentreraient disproportionnellement les "No Driver Found" — signe d'une offre de chauffeurs mal répartie géographiquement.

3. **Saisonnalité et échec de trajet liés.**  
Les pics de demande (Durga Puja, décembre, vendredis 18h-19h) coïncideraient avec des taux d'annulation plus élevés, la demande dépassant l'offre de chauffeurs disponibles à ces moments précis.

4. **Le mode de paiement influence le comportement d'annulation.**  
Le paiement en cash (25 367 cas) serait associé à plus d'annulations par les chauffeurs que les paiements digitaux (UPI, cartes), par crainte d'impayé ou de manque de monnaie.  
Intestable car on n'a pas de moyen de paiement quand la course est annulée.  
*Mais on peut tester est-ce que le mode de paiement influence sur course complète/incomplète*

5. **Satisfaction et fiabilité vont de pair.**  
Les trajets avec une durée d'attente (VTAT) élevée auraient des notes clients plus basses. Un VTAT plus long augmente-t-il le risque d'annulation par le client ?

---

## Sous-problématiques

- **Concurrentielle** : Uber Flex peut-il vraiment concurrencer inDrive sans reproduire les mêmes risques pour les chauffeurs ?
- **Sociale/culturelle** : comment un acteur centralisé (algorithme de pricing unique) s'adapte-t-il à un pays fragmenté en dizaines de calendriers religieux et de pratiques de mobilité locales (rickshaws, vélos-taxis) ?
- **Infrastructurelle** : le développement des autoroutes nationales profite-t-il davantage aux trajets urbains courts (Auto/Go) ou aux trajets Intercity longue distance ?
- **Écologique** : avec seulement 170 millions de km sur 9,2 milliards parcourus en véhicules électriques (moins de 2 %), la trajectoire de transition électrique d'Uber en Inde est-elle crédible à moyen terme ?

---

## Hypothèses testées sur le CSV — résultats  

Six hypothèses ont été testées statistiquement sur les 150 000 réservations Delhi-NCR, pour tenter d'expliquer les 38 % d'échec.

| # | Hypothèse | Résultat | Détail |
|---|---|---|---|
| H1 | Le type de véhicule influence le taux d'annulation | ❌ **Réfutée** | Taux d'annulation quasi identique entre tous les véhicules (Auto, Sedan, Bike...), aucune différence notable entre low-cost et premium |
| H2 | La zone de pickup/drop influence le taux d'échec | ❌ **Réfutée** | Écart-type de 0,89 à 1,32 point autour de la moyenne sur 176 zones ; distribution resserrée, aucune zone ne se détache significativement |
| H3 | La saisonnalité (jour, heure, fêtes religieuses, mois) influence l'échec | ❌ **Réfutée** | Le **volume** suit bien un cycle horaire marqué (pic à 18h, creux nocturne) confirmant les recherches externes, mais le **taux d'échec** reste stable à ~38 % quels que soient le jour, l'heure, la fête (Durga Puja, Aïd) ou le mois — la plateforme absorbe la demande sans dégradation de fiabilité |
| H4 | Le mode de paiement influence le taux de trajets incomplets | ❌ **Réfutée** | Écart de seulement 0,23 point entre cash (8,88 %) et les autres modes de paiement (8,65-8,88 %) |
| H5 | Le temps d'attente (VTAT) influence l'annulation/la satisfaction | ✅ **Confirmée pour l'annulation client** / ❌ réfutée pour la note | VTAT moyen nettement plus élevé pour les annulations client (12,5 min) que pour les trajets complétés (8,5 min) — signal le plus net de toute l'analyse. En revanche, aucune corrélation entre VTAT/CTAT et la note finale des trajets complétés |
| H6 | La valeur/distance du trajet influence l'annulation chauffeur | ⚠️ **Non testable** | `booking_value` et `ride_distance` ne sont enregistrés qu'une fois le trajet démarré — donc absents au moment où le chauffeur décide d'annuler. Limite structurelle du dataset, pas un résultat |


---

<!-- ![alt text](image.png) -->


**La part la plus importante de l'échec — l'annulation par le chauffeur (18 % du total, presque la moitié des 38 %) — reste totalement inexpliquée** avec les variables disponibles (véhicule, zone, temps, paiement, attente). Aucune des variables testées n'influence ce comportement de façon significative.

**Un pont direct avec la recherche qualitative** : cette impossibilité de tester H6 fait directement écho au problème qu'**Uber Flex** cherche à résoudre — dans le modèle classique, le chauffeur découvre souvent la course sans connaître le tarif à l'avance, et peut être tenté d'annuler après coup plutôt que de refuser d'emblée en connaissance de cause. Le fait que notre dataset ne capture même pas cette information (valeur du trajet avant acceptation) illustre concrètement le angle mort que ce nouveau produit tente de combler.

La moitié de l'échec c'est l'annulation driver. 
38% d'échec sans doute structurel (rapport offre/demande de chauffeurs, écobomie du trajet pour le chauffeur).

Hypothèse plausible : un chauffeur annule plus souvent les trajets peu rémunérateurs ou trop courts (pas assez rentables comparé au temps perdu).
Anass a trouvé aussi qeu les chauffeurs demandent aux clients d'annuler la course pour se faire payer directement et coutourner la commison d'Uber qui est passé de 0 à 35%.

---

Mur méthodologique car on ne peut pas avec ces datas vérifier nos hypothèses car nous avons des données utilisables seulement ou presque quand la course ets achevée.  
Par exemple il est impossible de vérifier si le conducteur annule une course car il l'a jugé non rentable. On a aucun inf disponible pour savoir quand le conducteur décide d'annuler sa course.

---

## Limites de l'analyse à mentionner

2. **Données manquantes structurelles** : `booking_value`, `ride_distance`, `payment_method`, `customer_rating` ne sont enregistrés qu'à partir du démarrage effectif du trajet — impossible d'analyser les déterminants de l'annulation (client ou chauffeur) sur ces variables économiques.
3. **Granularité origine-destination** : le croisement pickup×drop_location est inexploitable statistiquement (médiane de 5 réservations par paire sur 30 564 paires uniques, aucune n'atteint 30 observations).

