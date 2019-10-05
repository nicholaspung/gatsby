---
title: Typography.js
---

## Using Typography.js in Gatsby

Typography.js is a JavaScript library that allows you to explore the typographic design of your website and define beautiful custom and pre-existing typographic themes. It allows you to change the font on your website with ease. Typography.js currently maintains over 30 themes for you to use. However, you can also define your own custom font themes if none of the available themes meet your requirements. To use Typography in your project, it will involve installing a [Gatsby plugin](https://www.gatsbyjs.org/packages/gatsby-plugin-typography/) and specifying a configuration object for Typography.

## Installing the Typography plugin 

Gatsby has the plugin `gatsby-plugin-typography` to help introduce Typography.js library to your project.

You can install the plugin and its peer dependencies into your project by running the command `npm install gatsby-plugin-typography react-typography typography --save`

After the installation of the plugin has completed, navigate to your `gatsby-config.js` file located in the root of your project's directory and add the plugin to the configuration:

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

- **pathToConfigModule** (string): The path to the file where you export your Typography configuration.
- **omitGoogleFont** (boolean, `default: false`): By default, Typography includes a helper that makes a request to Google's Font CDN for fonts you need. However, you might want to use your own fonts, either by injecting fonts or using a CDN of your choosing. By setting `omitGoogleFont: true`, gatsby-plugin-typography will skip adding the font helper. Instead, you will have to include the appropriate fonts yourself - see [Adding a Local Font](https://www.gatsbyjs.org/docs/recipes/#adding-a-local-font)

## Creating the Typography configuration

Now that you have added the plugin, create the directory `src/utils/` if it does not already exist in your project and add a new file name `typography.js`. This file will be used to specify the typography configuration and used as the path for the `pathToConfigModule` option that the plugin requires.

Inside the `typography.js` file you just created, you can now define your websites typography configuration. A basic typography.js configuration looks like this:

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

Font sizes of all elements in Typography.js grow and shrink in relation to the `baseFontSize` defined above. Try playing around with this value to see the visual difference it can make to your website.

A full list of options that can be specified when defining a new typography can be found at [Typography.js](https://kyleamathews.github.io/typography.js/).

## Installing Typography themes

Typography.js has some built in themes that can save time when defining your websites font styling. The Funston theme maintained by Typography is one such theme and can be installed from npm running the command: `npm install typography-theme-funston --save`

To use the theme, edit the `typography.js` file that you created before and inform typography of the new configuration:

```diff:title=src/utils/typography.js
import Typography from "typography";
// highlight-start
+ import funstonTheme from 'typography-theme-funston'
// highlight-end
const typography = new Typography(
// highlight-start
- {
-     baseFontSize: '18px',
-     baseLineHeight: 1.666,
-     headerFontFamily: ['Avenir Next', 'Helvetica Neue', 'Segoe UI', 'Helvetica', 'Arial', 'sans-serif'],
-     bodyFontFamily: ['Georgia', 'serif'],
- },
+ funstonTheme
// highlight-end
);

export default typography;
```

After completing the above steps, you can start the development server using the command `gatsby develop` and navigate to the local website `http://localhost:8000`. If all went well you should see the text on your website using the Funston typographic theme. If your fonts remains unchanged, remove all `font-family` calls in your CSS and check again.

To find more themes to install, check out the official [Typography.js](https://kyleamathews.github.io/typography.js/) website.
