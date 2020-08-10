---
title: E2E Account Settings
date: 2020-07-22
author: Giovanni Rago
githubUser: ragog
tags: 
  - E2E
  - File Upload
---

Most services allow users to manage their account settings. These oftentimes have far-reaching implications on how the user experiences the platform. Verifying that the account settings can be viewed and modified is key in making sure we are offering a smooth service.

## Steps

Account properties to verify can run the gamut from simple text to connected third party services. In this example, we will focus on a popular case: changing a profile image by uploading one of our own. 

On our [test site](https://danube-store.herokuapp.com/), such a test could look as follows:

:::: tabs :options="{ useUrlFragment: false }"
::: tab Puppeteer 
<<< @/blog/snippets/puppeteer/file-upload.js
:::

::: tab Playwright
<<< @/blog/snippets/playwright/file-upload.js
:::
::::

:::: tabs :options="{ useUrlFragment: false }"
::: tab MacOS
```shell script
USER_EMAIL=user@email.com USER_PASSWORD=supersecure1 FILE_PATH=file.jpg node file-upload.js
```
:::
::: tab Windows
```shell script
SET USER_EMAIL=user@email.com
SET USER_PASSWORD=supersecure1
SET FILE_PATH=file.jpg
node file-upload.js
```
:::
::::

Here, we are simply checking for a message giving us feedback on the status of the upload. Depending on the website we are testing, it might be possible to also download the profile image afterwards to run a comparison locally for a more robust check.

## Takeaways
1. Use environment variables to inject secrets.
2. Use `uploadFile` (Puppeteer) or `setInputFiles` (Playwright) to upload the file.
3. If possible, download the file from the platform and compare it with the one that was just uploaded.