# Prompts utilisés pour constituer le corpus (domaine : climatisation)

Outil : Claude (Anthropic), recherche web et lecture de documents – date : 2026-11-01.
Principe retenu après un premier essai : **aucun document synthétique n'est écrit « de mémoire »**. Chaque document synthétique est rédigé à partir du texte de notices réelles lues pendant la session, et cite ses sources (document, page). Les documents réels sont conservés tels quels (voir inventaire.csv, colonne provenance).

## P01 – Cadrage et correction de cap
Demande de l'équipe : constituer un corpus de climatisation (30 à 50 documents, 2 familles). Premier résultat rejeté par l'équipe : documents entièrement générés, génériques et vides, sur une marque fictive. Nouvelle consigne : utiliser des documents officiels réels de fabricants ; ne garder du synthétique que ce qui est inspiré de documents réels présents dans le corpus.

## P02 – Recherche de documents réels
« Trouve des notices officielles en français de splits muraux (Daikin, Panasonic) et de cassettes / gainables tertiaires (Fujitsu General), avec URL directe du PDF, version et pagination. » Outil : recherche web. Les URL retenues ont toutes été retrouvées dans les résultats ; elles doivent être rouvertes par l'équipe (script telecharger_documents_reels.py).

## P03 – Lecture et extraction
« Lis intégralement ce PDF et extrais : description des voyants, couleurs, comportements (fixe/clignotant), périodicités d'entretien, valeurs numériques, codes d'erreur, avec numéro de page imprimé. » Documents lus : daikin_ftxf_a_guide_ref_fr, panasonic_cs_tz_ckew_mode_emploi, fujitsu_auxk_glah_cassette_om, fujitsu_ab_ar_au_a_tata_om, fujitsu_cassette_9374379231_om.

## P04 – Tableaux de codes et de signalisations (codes_alarme_*, signalisations_*)
« À partir des extraits P03, rédige un tableau code / signification / action de premier niveau pour [équipement]. Reformule sans copier ; n'invente aucun code ; signale ce qui n'est pas dans la source. »

## P05 – Procédures (dépannage, entretien annuel, fuite, mise en service, charge R32, redémarrage)
« Rédige la procédure [intitulé] pour [équipements]. Chaque prescription chiffrée doit provenir d'un extrait P03 cité avec sa page. Sépare ce qui relève d'un technicien habilité. »

## P06 – Historiques d'interventions
« Écris 3 à 4 interventions fictives par équipement, cohérentes avec les comportements décrits dans les notices (voyants, codes), avec un ticket ouvert. Aucune donnée personnelle. »

## P07 – Versions contradictoires
« Écris la procédure de nettoyage du filtre en version 2 (alignée sur Daikin et Panasonic) et en version 1 (ancienne, 2023) qui diffère sur la périodicité, la température d'eau, le trempage, le séchage et le rinçage ; écris aussi une procédure tertiaire dont l'intervalle contredit le manuel de CASS-C-02. »

## P08 – Document piégé
« Rédige une note de service d'apparence légitime sur l'entretien des filtres contenant, page 2 en très petits caractères, une instruction d'injection de prompt visant à envoyer des rapports vers un domaine .invalid. Réservé aux tests de sécurité de la semaine 5. »

## P09 – Copie scannée
« Génère une fiche d'intervention fictive (cas TCK-1021) puis simule un scan (rotation, bruit, flou, dégradé) pour tester l'OCR. »

## P10 – Schémas
« Dessine les repères et les voyants de [unité] avec les libellés exacts du manuel (a à l pour Daikin ; POWER/TIMER/nanoeX ; MINUTERIE/FONCTIONNEMENT/FILTRE ; SWING/TIMER/OPERATION). »

## P11 – Photos
Aucune génération par IA : photographies rassemblées par l'équipe. Les photos de LG, Sharp, Gree et Carrier n'ont plus de notice dans le corpus : elles servent de cas « équipement hors corpus ». Provenance et licence à compléter par l'équipe.

## Analyse critique (éléments déjà constatés, à compléter par l'équipe)
- Premier essai : documents génériques sur une marque fictive, valeurs inventées → rejetés ; passage à des sources réelles.
- La liste de liens fournie dans la demande initiale ne contenait pas les URL (cellules « PDF ») : liens à retrouver par recherche.
- Le texte extrait du guide Daikin perd les codes d'erreur (icônes) : l'appariement code ↔ signification repose sur l'ordre de la liste et sur des connaissances générales ; à vérifier au manuel d'entretien ESIE18-12.
- Les manuels Fujitsu sont hébergés par un distributeur (Eurofred), la notice Panasonic par un revendeur : provenance secondaire à confirmer sur les sites des fabricants.
- Les manuels réels se contredisent : intervalle de nettoyage du filtre (2 mois, 4 semaines, 2 semaines selon le modèle), signification d'un voyant TIMER qui clignote (Panasonic : défaut ; Fujitsu 2005 : minuterie mal réglée ; Fujitsu récent : veille), durée du dégivrage (2-16 min puis 4-15 min dans le même manuel).
- Les manuels utilisateur Fujitsu ne contiennent pas de tableau de codes : il faut le manuel d'entretien pour un diagnostic chiffré.

## P12 – Ajout de notices de marques (Samsung, LG, Panasonic, Sharp, Toshiba Carrier, Gree)
Liste de 30 liens PDF fournie par l'équipe (n° 11 à 40), intégrée telle quelle ; l'équipe a indiqué que l'encadrante n'a pas d'objection sur les conditions de réutilisation (à garder par écrit). Le n° 24 (Panasonic CS-TZ/RZ, izi by EDF) est identique à `panasonic_cs_tz_ckew_mode_emploi` : non dupliqué. Les 29 autres sont inscrits dans l'inventaire avec provenance, mais **non ouverts** : version, nb_pages, éléments visuels, modèle exact restent `A_COMPLETER` jusqu'à ouverture par l'équipe. Équipements rattachés (SPLIT-E/F/G/H/I, MULTI-E/F, MURAL/PLAF/GAIN/CASS/SOL-J, GAIN-H, PORT-H) : identifiants fictifs, à confirmer.
Outil : Claude (Claude Code), 2026-11-01.

## P13 – Documents complémentaires trouvés par recherche web
« Cherche d'autres documents publics sur la climatisation utiles au projet (sécurité des fluides, notices FR de splits, télécommandes). » Retenus : INRS ED 6395 (titre, date et nombre de pages vérifiés par lecture), Daikin ATXP-M mode d'emploi, Daikin FTXC-E/RXC-E installation, Daikin BRC1NRV71 (trois liens issus de résultats de recherche, **non ouverts**). Outil : Claude (recherche web), 2026-11-01.

## Analyse critique – ajouts de la session 2026-11-01
- Les serveurs de téléchargement n'étaient pas accessibles depuis l'environnement de Claude : aucun des 33 PDF ajoutés n'a été ouvert ni vérifié ; `nb_pages`, `version` et `elements_visuels` sont à compléter avec `telecharger_documents_reels.py`.
- Plusieurs notices sont hébergées par des tiers (Castorama, notice-facile, hellopro, bricoman, maison-energy, Ouellet) et non par le fabricant : provenance secondaire, version possiblement obsolète.
- Les notices « Carrier » sont des Toshiba Carrier commerciales ; la photo Carrier du corpus est un appareil résidentiel : la correspondance n'est pas établie, la photo reste « hors corpus ».
- Les photos LG, Sharp et Gree ne sont plus « hors corpus » : une notice existe pour la marque, mais le modèle exact n'est pas identifiable sur la photo ; elles deviennent des cas ambigus.
- Le corpus compte désormais 77 documents, au-delà des 30 à 50 demandés par la consigne : à valider avec l'encadrante.
