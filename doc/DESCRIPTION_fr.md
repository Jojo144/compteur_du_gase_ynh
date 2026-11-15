Le compteur du GASE est une application web qui permet de gérer les cagnottes et le stock d'un GASE (*Groupement d'Achat en Service Épicerie*), une épicerie autogérée.

### Permissions

L'application a trois permissions, définies à l'installation et modifiables dans *Utilisateurs > Gérer les groupes et les permissions* :

- **Page d'accueil** (`home_page`) : la page d'accueil avec les prochaines permanences. Si elle est ouverte aux *visiteurs*, les téléphones et emails restent masqués pour les personnes non connectées.
- **Principale** (`main`) : le reste de l'application (achats, cagnottes, stock…). Elle est nécessaire pour voir les téléphones et emails sur la page d'accueil.
- **Panneau d'administration** (`admin`) : l'interface d'administration Django, réservée par défaut au groupe *admins*.

Voici les cas d'usage imaginés (*frodon* et *gandalf* sont des utilisateurs ou des groupes) :

| Permission home_page | Permission main | Permission admin |                                                                                                                                          |
|----------------------|-----------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| visitors             | visitors        | visitors         | tout le monde a accès à tout                                                                                                             |
| visitors             | visitors        | frodon           | tout le monde a accès à tout sauf à l'admin                                                                                              |
| visitors             | frodon          | frodon           | tout le monde a accès à la page d'accueil (sans les numéros de tel) et frodon a accès à tout                                             |
| visitors             | frodon          | gandalf          | tout le monde a accès à la page d'accueil (sans les numéros de tel), frodon a accès au site mais pas à l'admin et gandalf a accès à tout |
| frodon               | frodon          | frodon           | seul frodon a accès au site (admin incluse)                                                                                              |
| frodon               | frodon          | gandalf          | seul frodon et gandalf ont accès au site et seulement gandalf à l'admin                                                               |
