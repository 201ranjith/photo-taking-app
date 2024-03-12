Photo-Taking-App- with Ionic Framework


Build Your First Ionic Mobile App: Angular Development Tutorial
  <meta
    name="description"
    content="Ionic's single codebase builds for any platform using just HTML, CSS, & JavaScript. Develop your first mobile app with our step-by-step Angular tutorial."
  />
</head>

The great thing about Ionic is that with one codebase, you can build for any platform using just HTML, CSS, and JavaScript. Follow along as we learn the fundamentals of Ionic app development by creating a realistic app step by step.

Here’s the finished app running on all 3 platforms:
 
Youtube Link: "https://www.youtube.com/embed/0ASQ13Y1Rk4"
  

note
Looking for the previous version of this guide that covered Ionic 4 and Cordova? [See here.](../developer-resources/guides/first-app-v4/intro.md)


## What We'll Build

We'll create a Photo Gallery app that offers the ability to take photos with your device's camera, display them in a grid, and store them permanently on the device.

Highlights include:

- One Angular-based codebase that runs on the web, iOS, and Android using Ionic Framework [UI components](https://ionicframework.com/docs/components).
- Deployed as a native iOS and Android mobile app using [Capacitor](https://capacitorjs.com), Ionic's official native app runtime.
- Photo Gallery functionality powered by the Capacitor [Camera](https://capacitorjs.com/docs/apis/camera), [Filesystem](https://capacitorjs.com/docs/apis/filesystem), and [Preferences](https://capacitorjs.com/docs/apis/preferences) APIs.

Find the complete app code referenced in this guide [on GitHub](https://github.com/ionic-team/photo-gallery-capacitor-ng).

## Download Required Tools

Download and install these right away to ensure an optimal Ionic development experience:

- **Node.js** for interacting with the Ionic ecosystem. [Download the LTS version here](https://nodejs.org/en/).
- **A code editor** for... writing code! We are fans of [Visual Studio Code](https://code.visualstudio.com/).
- **Command-line interface/terminal (CLI)**:
  - **Windows** users: for the best Ionic experience, we recommend the built-in command line (cmd) or the Powershell
    CLI, running in Administrator mode.
  - **Mac/Linux** users, virtually any terminal will work.

## Install Ionic Tooling

Run the following in the command line terminal to install the Ionic CLI (`ionic`), `native-run`, used to run native binaries on devices and simulators/emulators, and `cordova-res`, used to generate native app icons and splash screens:

note
To open a terminal in Visual Studio Code, go to Terminal -> New Terminal.

```shell
npm install -g @ionic/cli native-run cordova-res
```

note
The `-g` option means _install globally_. When packages are installed globally, `EACCES` permission errors can occur.

Consider setting up npm to operate globally without elevated permissions. See [Resolving Permission Errors](../developing/tips.md#resolving-permission-errors) for more information.


## Create an App

Next, create an Ionic Angular app that uses the “Tabs” starter template and adds Capacitor for native functionality:

```shell
ionic start photo-gallery tabs --type=angular --capacitor
```

This starter project comes complete with three pre-built pages and best practices for Ionic development. With common building blocks already in place, we can add more features easily!

Next, change into the app folder:

```shell
cd photo-gallery
```

Next we'll need to install the necessary Capacitor plugins to make the app's native functionality work:

```shell
npm install @capacitor/camera @capacitor/preferences @capacitor/filesystem
```

### PWA Elements

Some Capacitor plugins, including the Camera API, provide the web-based functionality and UI via the Ionic [PWA Elements library](https://github.com/ionic-team/ionic-pwa-elements).

It's a separate dependency, so install it next:

```shell
npm install @ionic/pwa-elements
```

Next, import `@ionic/pwa-elements` by editing `src/main.ts`.

```tsx
import { defineCustomElements } from '@ionic/pwa-elements/loader';

// Call the element loader before the bootstrapModule/bootstrapApplication call
defineCustomElements(window);
```

That’s it! Now for the fun part - let’s see the app in action.

## Run the App

Run this command next:

```shell
ionic serve
```

And voilà! Your Ionic app is now running in a web browser. Most of your app can be built and tested right in the browser, greatly increasing development and testing speed.
