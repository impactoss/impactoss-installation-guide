# Labels & translations

#### Labels & text files

Labels and text used by the client application are defined for the default language English - Great Britain ("en-GB") in folder
[/app/translations](https://github.com/impactoss/impactoss-client/tree/master/app/translations).

You can update all application text and labels for your language (default "en-GB.json") in [/app/themes/config.js](https://github.com/impactoss/impactoss-client/blob/master/app/themes/config.js) (see [General application settings](/client-config/application.md)).

Specifically you should update or review the following labels:
- Contact email: `"app.components.Footer.contact.email"` and `"app.components.Footer.contact.anchor"`
- Publisher website: `"app.components.Footer.responsible.url"` and `"app.components.Footer.responsible.anchor"`
- Partner and sponsor names and website addresses (if not [disabled in app settings](/client-config/application.md))): `"app.components.Footer.partners.title[No]"` and `"app.components.Footer.partners.url[No]"` for every partner (number of partners determined in themes file, see [Themes](/client-config/theme.md))
- Application title (home page): `"app.containers.App.app.title"`
- Application claim (home page): `"app.containers.App.app.claim"`
- Taxonomy groupings according to [Category groupings & categories](/client-config/categories.md): `app.containers.App.taxonomyGroups.[No]` where "No" matches the group id
- Taxonomy titles and labels for each taxonomy set up (see [Category groupings & categories](/client-config/categories.md)): `"app.containers.App.entities.taxonomies.[No].[type]"` where "[No]" is the server ID and "[type]" one off "single", "plural", "shortSingle", "shortPlural", "description" and "empty" ("description" is shown on category overview page)
- Home page meta title: `"app.containers.HomePage.pageTitle"`
- Home page meta description: `"app.containers.HomePage.pageDescription"`

#### Translate to other languages

Translation files to other languages can be added here according to the default locale defined in [/app/themes/config.js](https://github.com/impactoss/impactoss-client/blob/master/app/themes/config.js).