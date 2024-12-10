---
icon: message-question
---

# Support

Contact Support

Email: [hello@softstack.io](mailto:hello@softstack.io)\
Telegram: [@yannikheinze](https://t.me/yannikheinze)

\
Request API key:  [https://swfe3fmu6fc.typeform.com/to/qP56yNc5](https://swfe3fmu6fc.typeform.com/to/qP56yNc5)

### FAQ

<details>

<summary>Q1: Which wallets are supported?</summary>

A: Refer to the Supported Wallets section for a list of compatible wallets.

</details>

<details>

<summary>Q2: How do I obtain an API key?</summary>

A: Use our Typeform to obtain an API key [https://swfe3fmu6fc.typeform.com/to/qP56yNc5](https://swfe3fmu6fc.typeform.com/to/qP56yNc5)&#x20;

</details>

<details>

<summary>Q3: What if I encounter an error during installation?</summary>

A: Ensure all prerequisites are met and consult the documentation. If issues persist, contact [support](support.md).

</details>

<details>

<summary>Q4: What can I do if I use Next.js and have problems loading the modal's images?</summary>

If you're using Next.js and have problems loading the modal's images, make sure to update your `next.config.js` to properly handle image assets. Specifically, add custom Webpack rules to process SVG and PNG files as `asset/resource`and ensure the correct `publicPath` and `outputPath` are set. This helps Next.js locate the images correctly and avoids caching issues or incorrect paths.

</details>

<details>

<summary>Q5: Webpack is missing a module?</summary>

Starting with Webpack 5, automatic support for Node.js core modules like `buffer` or `stream` was removed. This change was made because these modules are often not needed in browser environments. Instead, developers need to manually configure polyfills for these modules. This approach helps reduce bundle size and better aligns with modern web standards.

</details>

