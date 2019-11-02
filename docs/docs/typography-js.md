---
title: Typography.js
---

## Using Typography.js in Gatsby

Typography.js is a JavaScript library that allows you to explore the typographic design of your website and define beautiful custom and pre-existing typographic themes. It enables you to change the font on your website with ease. Typography.js currently maintains over 30 themes for you to use. You can also create your own custom font themes if no available themes fit your requirements. To use Typography in your project, you will be installing a [Gatsby plugin](https://www.gatsbyjs.org/packages/gatsby-plugin-typography/) and specifying a configuration object for Typography.

## Installing the Typography plugin

Gatsby has the plugin `gatsby-plugin-typography` to integrate Typography.js into your project.

You can install the plugin and its peer dependencies into your project by running the command `npm install gatsby-plugin-typography react-typography typography --save`

After the installation of the plugin is complete, navigate to your `gatsby-config.js` file located in the root of your project's directory and add the plugin to the configuration:

```js:title=gatsby-config.js
module.exports = {
  plugins: [
    // highlight-start
    {
      resolve: `gatsby-plugin-typography`,
      options: {
        pathToConfigModule: `src/utils/typography`,
      },
    },
    // highlight-end
  ],
}
```

`gatsby-plugin-typography` takes two options for you to specify:

<<<<<<< HEAD
- **pathToConfigModule** (string): The path to the file where you export your Typography configuration.
- **omitGoogleFont** (boolean, `default: false`): By default, Typography includes a helper that makes a request to Google Font's CDN for fonts you need. You may want to use your own fonts, either by injecting fonts or using a CDN of your choosing. By setting `omitGoogleFont: true`, `gatsby-plugin-typography` will skip adding the font helper. Instead, you will have to include the appropriate fonts yourself - see [Adding a Local Font](https://www.gatsbyjs.org/docs/recipes/#adding-a-local-font).
||||||| merged common ancestors
- **pathToConfigModule**: (string) The path to the file in which you export your typography configuration.
- **omitGoogleFont**: (boolean, default: false) Typography includes a helper that makes a request to Google’s font CDN for the fonts you
  need. You might, however, want to inject the fonts into JS or use a
  CDN of your choosing. Setting this value to true will make
  gatsby-plugin-typography skip the inclusion of this helper. You will
  have to include the appropriate fonts yourself.
=======
- **pathToConfigModule** (string): The path to the file where you export your Typography configuration.
- **omitGoogleFont** (boolean, `default: false`): By default, Typography includes a helper that makes a request to Google Font's CDN for fonts you need. You may want to use your own fonts, either by injecting fonts or using a CDN of your choosing. By setting `omitGoogleFont: true`, `gatsby-plugin-typography` will skip adding the font helper. Instead, you will have to include the appropriate fonts yourself - see [Adding a Local Font](https://www.gatsbyjs.org/docs/recipes/#adding-a-local-font)
>>>>>>> 3aa41fb8dbf7fe294f35a706424c6b2b11345881

## Creating the Typography configuration

Now that you have added the plugin, create the directory `src/utils/` if it does not already exist in your project and add a new file named `typography.js`. You will use this file to specify the Typography configuration and set this file to be the path for the `pathToConfigModule` option.

Inside the `typography.js` file you created, you define your website's typography configuration. A basic typography.js configuration looks like this:

```js:title=src/utils/typography.js
import Typography from "typography"

const typography = new Typography({
  baseFontSize: "18px",
  baseLineHeight: 1.666,
  headerFontFamily: [
    "Avenir Next",
    "Helvetica Neue",
    "Segoe UI",
    "Helvetica",
    "Arial",
    "sans-serif",
  ],
  bodyFontFamily: ["Georgia", "serif"],
})

export default typography
```

If you're installing Typography.js into an existing Gatsby project you've started, you will need to delete all conflicting CSS font styles from your codebase in favor of your new Typography.js settings.

Font sizes of all elements in Typography.js grow and shrink in relation to the `baseFontSize` defined above. Try playing around with this value and see the visual difference it can make to your website.

To find or create a new typography theme, you can visit [Typography.js](https://kyleamathews.github.io/typography.js/) to see a list of options.

## Installing Typography themes

Typography.js has built in themes that can save time when defining your website's font styling. The Funston theme, maintained by Typography, is one of the built in themes. To install the Funston theme from npm, run the command: `npm install typography-theme-funston --save`

To use the theme, edit the `typography.js` file that you created before and inform Typography of the new configuration:

```diff:title=src/utils/typography.js
import Typography from "typography";
// highlight-start
+ import funstonTheme from 'typography-theme-funston'
// highlight-end
const typography = new Typography(
- {
-     baseFontSize: '18px',
-     baseLineHeight: 1.666,
-     headerFontFamily: ['Avenir Next', 'Helvetica Neue', 'Segoe UI', 'Helvetica', 'Arial', 'sans-serif'],
-     bodyFontFamily: ['Georgia', 'serif'],
- },
// highlight-start
+ funstonTheme
// highlight-end
);

export default typography;
```

<<<<<<< HEAD
After completing the above steps, you can start the development server using the command `gatsby develop` and navigate to the local website `http://localhost:8000`. If all went well you should see the text on your website using the Funston typographic theme.
||||||| merged common ancestors
After completing the above steps, you can start the development server using the command `gatsby develop` and navigate to the local website `http://localhost:8000`. If all went well you should see the text on your website using the Funston typographic theme just installed.
=======
After completing the above steps, you can start the development server using the command `gatsby develop` and navigate to the local website <http://localhost:8000>. If all went well you should see the text on your website using the Funston typographic theme.

**Note**: If your fonts remains unchanged, remove all `font-family` calls in your CSS and check again.
>>>>>>> 3aa41fb8dbf7fe294f35a706424c6b2b11345881

<<<<<<< HEAD
**Note**: If your fonts remains unchanged, remove all `font-family` calls in your CSS and check again.

To find more themes to install, check out the official [Typography.js](https://kyleamathews.github.io/typography.js/) website.
||||||| merged common ancestors
If you would like to find more themes to install into your project check out at the official [Typography.js](https://kyleamathews.github.io/typography.js/) website.
=======
To find more themes to install, check out the official [Typography.js](https://kyleamathews.github.io/typography.js/) website.
>>>>>>> 3aa41fb8dbf7fe294f35a706424c6b2b11345881
