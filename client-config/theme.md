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

#### Media files

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
