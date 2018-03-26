# Client settings

The application configuration file is
[/app/themes/config.js](https://github.com/impactoss/impactoss-client/blob/master/app/themes/config.js).

#### Must: server endpoint

Please set server api endpoint `ENDPOINTS > API` to your (custom) server endpoint set up as part of your [Heroku installation](/server-installation/heroku.md)

In addition there are several other optional settings (in order of appearance):

#### Optional: language and date settings

- Language locale: If you plan to translate the application to another language, you must set the language locale `DEFAULT_LOCALE`, also see [Labels](/client-config/locale.md)
- Date format: update `DATE_FORMAT` to change the deault date format `'dd/mm/yyyy'`

#### Optional: enable/disable partners and sponsors

- Set `SHOW_FOOTER_PARTNERS` to `true` or `false`;
- Partner names and website addresses can be set up in the language file, see [Labels]((/client-config/locale.md))
- Partner logos can be added to the media folder, see [Theme](/client-config/theme.md)

#### Optional: enable/disable SDG component

- Set `ENABLE_SDGS` to `true` or `false` to enable or disable the SDG component
- Please make sure to also add/uncomment or remove/outcomment (`// `) the 4 SDG tables from the `DB_TABLES` object:
  - Enabled:
  ```
  export const DB_TABLES = [
    ...
    'sdgtarget_categories',
    'sdgtarget_indicators',
    'sdgtarget_measures',
    'sdgtargets',
  ];
  ```
  - Disabled:
  ```
  export const DB_TABLES = [
    ...
    // 'sdgtarget_categories',
    // 'sdgtarget_indicators',
    // 'sdgtarget_measures',
    // 'sdgtargets',
  ];
  ```

#### Optional: enable (or disable) additional fields for Action entity

There are 2 additional fields for action entities that are disabled by default:
- Outcome (`attribute: 'outcome'`) which can be used to describe the desired or achieved outcome of an action. To enable set `disabled: false` or delete the line `disabled: true`.
- Indicator summary (`attribute: 'indicator_summary'`) which can be used to summarise the associated indicators or their purpose. To enable set `disabled: false` or delete the line `disabled: true`.
