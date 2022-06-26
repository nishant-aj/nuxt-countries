# Start with Nuxt3

## Table of Contents

- [Installation](#installation)
- [Verify your installation](#verify-your-installation)
- [Creating your Nuxt project](#creating-your-nuxt-project)
- [The app.vue file](#the-appvue-file)
- [Running your project](#running-your-project)

## Installation

You would need to download the following:

- [Nodejs](https://nodejs.org/en/download/)
- [Git](https://git-scm.com/downloads)
- [Visual Studio (or any other Text Editor/IDE)](https://code.visualstudio.com)

## Verify your installation

Open the terminal on your system and run the following commands separately:

```bash
node -v
npm -v
git --version
```

You should be able to see the version numbers after entering each command. If you do not, you haven't installed the requirements properly.

## Creating your Nuxt Project

Enter into your directory where you wish to create the project. Run the following command:

```bash
npx nuxt init <project-name>
```

In our case, the `project-name` shall be countries. So you should run:

```bash
npx nuxi init countries
cd countries
npm install
```

After creating the project, enter into the directory and install the required dependencies.

## The app.vue file

The app.vue file is specific to Nuxt. Anything and Everything we code in the `app.vue` file shall be rendered on the website.

## Running your project

To view your development, run the following command:

```bash
npm run dev
```

and this will start your project server. After the Nitro server has successfully started, you can view your website on this [link](https://localhost:3000) in your browser.
