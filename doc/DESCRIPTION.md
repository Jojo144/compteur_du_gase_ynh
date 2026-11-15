Le compteur du GASE is a web application to manage the kitties and the stock of a GASE (*Groupement d'Achat en Service Épicerie*, "Grocery Service Purchasing Group" in English), a self-managed grocery store.

### Permissions

The app has three permissions, set at install time and editable in *Users > Manage groups and permissions*:

- **Home page** (`home_page`): the home page with the upcoming shifts. When open to *visitors*, phone numbers and emails stay hidden from anonymous users.
- **Main** (`main`): the rest of the app (purchases, kitties, stock…). It is required to see phone numbers and emails on the home page.
- **Administration panel** (`admin`): the Django administration interface, restricted to the *admins* group by default.

Here are the intended use cases (*frodon* and *gandalf* are users or groups):

| home_page permission | main permission | admin permission |                                                                                                                                         |
|----------------------|-----------------|------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| visitors             | visitors        | visitors         | everyone can access everything                                                                                                          |
| visitors             | visitors        | frodon           | everyone can access everything except the admin                                                                                         |
| visitors             | frodon          | frodon           | everyone can access the home page (without phone numbers) and frodon can access everything                                              |
| visitors             | frodon          | gandalf          | everyone can access the home page (without phone numbers), frodon can access the site but not the admin, and gandalf can access everything |
| frodon               | frodon          | frodon           | only frodon can access the site (admin included)                                                                                        |
| frodon               | frodon          | gandalf          | only frodon and gandalf can access the site, and only gandalf the admin                                                                 |
