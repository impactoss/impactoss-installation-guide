# Application theme

In the application theme folder ([/app/themes/](https://github.com/impactoss/impactoss-client/tree/master/app/themes)) are
- one or more theme files (e.g. the base theme [/app/themes/theme-base.js](https://github.com/impactoss/impactoss-client/blob/master/app/themes/theme-base.js)) that control the theme and determine the application branding,
- an icons file  ([/app/themes/icons.js](https://github.com/impactoss/impactoss-client/blob/master/app/themes/icons.js)) for all icons including the taxonomy icons
- a media folder ([/app/themes/media/](https://github.com/impactoss/impactoss-client/tree/master/app/themes/media)) for all brand and partner images
- the application configuration file ([/app/themes/config.js](https://github.com/impactoss/impactoss-client/blob/master/app/themes/config.js)), also see [General application settings](/client-config/application.md)

### Principal theme file

To customise the default theme you can either
- edit the existing base theme file (theme-base.js), or
- edit your own copy.

When creating a copy please make sure to update the theme file in [/app/app.js](https://github.com/impactoss/impactoss-client/blob/master/app/app.js) to reference the filename of your copy: `import theme from 'themes/theme-base';`.

The theme file specifies the following:

#### Media file references

All image files from the "/app/themes/media/" folder, including up to 6 partner logos if enabled (see [Settings]((/client-config/application.md))), must be imported (e.g. `import headerLogo from 'themes/media/headerLogo.png';`) and referenced in the global media object:
```
theme.media = {
  headerLogo: [headerLogo, headerLogo2x],
  graphicHome: [graphicHome, graphicHome2x],
  titleHome: [titleHome, titleHome2x],
  impactossLogo: [impactossLogo, impactossLogo2x],
  // up to 6 partner logos,
  // link text and title to be set in translations/[lang].js > app.components.Footer.partners.[]
  partnerLogos: [
    [partner1, partner1x2x],
    [partner2, partner2x2x],
    [partner3, partner3x2x],
    [partner4, partner4x2x],
  ],
};
```

> Note: in addition to the regular image, it is reocmmended to provide a high resolution "retina" image identified by the "@2x" in the filename and the `2x` in the variable name.

#### Colour palettes

You can set custom colours according to your branding requirements and design preferences in 4 principal colour palettes expressed either as an array of colours `[ "#111". ... ]` or using a Coolors URL e.g. `coolorsToHex('https://coolors.co/0063b5-0070cc-0077d8-ffffff-ffffff')`:
- primary brand colours `primary`: 4 custom colours plus white (dark to light)
- secondary brand colours `secondary`: 4 custom colours plus white (dark to light)
- dark grayscale `dark`: dark grays mainly used for text and dark design elements (incl. black if desired) (dark to light)
- light grayscale `light`: light grays mainly used for backgrounds (incl.white if desired) (light to dark)

In addition to the theme file, some default colours (like principal text, background and link coloours) are also set in [/app/global-styles.js](https://github.com/impactoss/impactoss-client/blob/master/app/global-styles.js))

> Note: please be aware of the required contrast ratio for accessibility requirements (for details see https://webaim.org/resources/contrastchecker/)

Additional colour palettes are:
- error colours `error` for error and warning messages
- success colours `success` for success and confirmation messages

These general palettes are then referenced (using palette name and colour index (e.g. `primary[4]`)) for general styles and specific UI elements. Some examples are:
- Text colours referencing "dark" and "primary" palettes: `text: [dark[0], dark[3], primary[4]]` (#primaryFont, #secondaryFont, #inverse)
- Default button referencing primary palette for text and background colours `buttonDefault: [primary[4], primary[2]]` ('#text', '#bg')

#### Taxonomy and entity colours

Specific colours are defined as arrays for each configured taxonomy (see [Categories](/client-config/categories.md)) where the array index (starting with 0) refers to the taxonomy id as set in the database (usually starting with 1):
- regular colours `taxonomies: [ '#unused', #taxon1, #taxon2, ... ]`
- hover colours `taxonoiesHover: [ '#unused', #taxon1, #taxon2, ... ]`

Additional colours are defined for inactive SMART criteria taxonomies (if configured)
```
smartInactive: [
    '#DBE1E1', // SMART inactive
    '#656F75', // SMART inactive hover
    '#9BABAB', // SMART inactive icon
],
```

> Note: again please be aware of any contrast ratio requirements (for details see https://webaim.org/resources/contrastchecker/)

Entity colours are defined for
- Actions `measures` and `measuresHover`
- Recommendations `recommendations` and `recommendationsHover`
- SDG Targets `sdgtargets` and `sdgtargetsHover`
- Indicators `indicators` and `indicatorsHover`
- SDG Targets `reports` and `reportsHover`
- User roles `roles` and `rolesHover`

Attribute colours
- General attributes `attributes` and `attributesHover`

#### Fonts

In addition to the primary font specified in the global styles file ([/app/global-styles.js](https://github.com/impactoss/impactoss-client/blob/master/app/global-styles.js)), fonts are defined by the `theme.fonts` object:
```
theme.fonts = {
  // also see global-styles.js for primary font
  pre: 'Consolas, Liberation Mono, Menlo, Courier, monospace',
  quote: 'Georgia, serif',
  title: 'Roboto, Helvetica Neue, Helvetica, Arial, sans-serif', // only used for fallback
  claim: 'Roboto, Helvetica Neue, Helvetica, Arial, sans-serif', // only used for fallback
};
```

#### Sizes

Text and other UI sizes are defined by the `theme.sizes` object. Please also check the global styles ([/app/global-styles.js](https://github.com/impactoss/impactoss-client/blob/master/app/global-styles.js)) and settings ([/app/themes/config.js](https://github.com/impactoss/impactoss-client/blob/master/app/themes/config.js)) files.

#### Patterns

Background patterns for header and sidebar headers can be defined as "datauris" in `themes.backgroundImages`.

Background patterns can be enabled in the settings file ([/app/themes/config.js](https://github.com/impactoss/impactoss-client/blob/master/app/themes/config.js)):
- show pattern in header: `SHOW_HEADER_PATTERN` (true/false)
- show pattern in sidebar headers: `SHOW_SIDEBAR_HEADER_PATTERN` (true/false)
- show header pattern behind home page graphic: `SHOW_HEADER_PATTERN_HOME_GRAPHIC` (true/false)

### Icons file

([/app/themes/icons.js](https://github.com/impactoss/impactoss-client/blob/master/app/themes/icons.js))

For each icon one or more SVG-paths are required and optionally also the viewport size (defaults to 24px)
```
iconName: {
 size: 24,
 paths: ['s v g', 'p a t h s'],
}
```

#### Taxonomy icons

Icons are specified for each taxonomy and should be configured to match your taxonomy set up ([Categories](/client-config/categories.md))), where the name references the server taxonomy id e.g. the "Reporting cycle" icon assuming that the taxonomy id is "2":
```
taxonomy_2: {
  size: 40,
  paths: [
    'M32.5,20A12.51,12.51,0,0,1,22,32.32V36l-8-5,8-5v3.28A9.49,9.49,0,0,0,25,12l2-1.26.73-.46A12.48,12.48,0,0,1,32.5,20Zm-22,0A9.51,9.51,0,0,1,18,10.72V14l8-5L18,4V7.68a12.48,12.48,0,0,0-5.79,22.08l.73-.46L15,28A9.49,9.49,0,0,1,10.5,20Z',
  ],
},
```

#### Entity icons

Entity icons are:
- Actions `measures`
- Recommendations `recommendations`, `recommendationAccepted`, `recommendationNoted`
- SDG Targets `sdgtargets`
- Indicators `indicators`
- SDG Targets `reports`
- User roles `roles`

### Media files

The media folder ([/app/themes/media/](https://github.com/impactoss/impactoss-client/blob/master/app/themes/media/)) contains several image files (both regular and "retina" resolutions ("@2x" for retina)) that you can either replace or add to (remember: image files need to be referenced in the theme file):
- "headerLogo.png": the logo image shown in the header. In the config file([/app/themes/config.js](https://github.com/impactoss/impactoss-client/blob/master/app/themes/config.js)) set `SHOW_HEADER_TITLE` to `false` if the logo contains the application title or to `true` if not.
- "homeGraphic.png": principal graphic on home page
- "homeTitle.png": title graphic on home page when `SHOW_HOME_TITLE` set to `false`.
- "impactoss.png": IMPACT OSS platform graphic shown in the Footer
- serveral partner logos if `SHOW_FOOTER_PARTNERS` enabled in ([/app/themes/config.js](https://github.com/impactoss/impactoss-client/blob/master/app/themes/config.js))
