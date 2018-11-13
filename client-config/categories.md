### Optional: Taxonomies

In addition to setting up the taxonomies on the server (see [Category groupings & categories](/server-config/categories.md)), you will need to configure them also on the client.

This requires the following:
- set up taxonomy groups (see below)
- set up taxonomy titles and labels (see [Labels](/client-config/locales.md))
- set up taxonomy colours and icons (see [Themes](/client-config/theme.md))

> Note: as for the server code there is also a minimal set-up in the "lite" branch in addition to the default configuration in the "master" branch

---

#### Taxonomy groups

You can set up to 4 taxonomy groups in the configuration file
[/app/themes/config.js](https://github.com/impactoss/impactoss-client/blob/master/app/themes/config.js) by setting the lower and upper priority numbers assigned on the server.

By default there are two groupings set up, one for priority values 0 to 9 and one for values 10 to 19. Here is the code (where id matches the id referenced in the translations file, see [Labels](/client-config/locales.md)):

```
export const TAXONOMY_GROUPS = [
  {
    id: 1,
    priorityMin: 0,
    priorityMax: 9,
    default: true,
  },
  {
    id: 2,
    priorityMin: 10,
    priorityMax: 19,
  },
];
```
