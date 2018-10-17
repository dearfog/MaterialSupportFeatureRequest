I have checked by creating new app with Ionic + Angular 6 and using Angular Schematics i have added Angular Material and successfully added dashboard using official Angular Schematics, Every things works fine, My Request is to add new **type** flag as **--type=angular-material**. I am positing all of the steps and a repo link for demo.

#Steps to follow : 
 1. Create new project `ionic start <project-name> --type=angular`
 2. Go to your project dir and add @angular/material using schematics  `ng add @angular/material`
 3. Generate Side-Nav bar and dashboard `ng generate @angular/material:material-nav --name shared/components/layout` `ng generate @angular/material:material-dashboard --name components/dashboard`
 4. Add Router Outlet to layout component for child routing, `<router-outlet></router-outlet>`;
 5. Change Routes in app.routing.module as below 

```
    {   path: '', redirectTo: '/dashboard', pathMatch: 'full' },
    { 
        path: '', 
        component: LayoutComponent,
        children:[
            { path: 'home', loadChildren: './home/home.module#HomePageModule' },
            { path: 'dashboard', component:DashboardComponent},
        ]
    },
``` 
This is the full output in terminal

```
nasiruddin@nasiruddin-PC:~/Desktop/Oct-10$ ionic start --type=angular

Every great app needs a name! 😍

Please enter the full name of your app. You can change this at any time. To bypass this prompt next time, supply name, 
the first argument to ionic start.

? Project name: MaterialSupportFeatureRequest

Let's pick the perfect starter template! 💪

Starter templates are ready-to-go Ionic apps that come packed with everything you need to build your app. To bypass this 
prompt next time, supply template, the second argument to ionic start.

? Starter template: blank
✔ Preparing directory ./MaterialSupportFeatureRequest - done!
✔ Downloading and extracting blank starter - done!
? Integrate your new app with Cordova to target native iOS and Android? Yes
> ionic integrations enable cordova --quiet
[INFO] Downloading integration cordova
[INFO] Copying integrations files to project
[OK] Integration cordova added!

Installing dependencies may take several minutes.

     ✨   IONIC  DEVAPP   ✨

 Speed up development with the Ionic DevApp, our fast, on-device testing mobile app

  -  🔑   Test on iOS and Android without Native SDKs
  -  🚀   LiveReload for instant style and JS updates

 -->    Install DevApp: https://bit.ly/ionic-dev-app    <--

────────────────────────────────────────────────────────────

> npm i

> node-sass@4.9.4 install /home/nasiruddin/Desktop/Oct-10/MaterialSupportFeatureRequest/node_modules/node-sass
> node scripts/install.js

Cached binary found at /home/nasiruddin/.npm/node-sass/4.9.4/linux-x64-64_binding.node

> circular-json@0.5.7 postinstall /home/nasiruddin/Desktop/Oct-10/MaterialSupportFeatureRequest/node_modules/circular-json
> echo ''; echo "\x1B[1mCircularJSON\x1B[0m is in \x1B[4mmaintenance only\x1B[0m, \x1B[1mflatted\x1B[0m is its successor."; echo ''


\x1B[1mCircularJSON\x1B[0m is in \x1B[4mmaintenance only\x1B[0m, \x1B[1mflatted\x1B[0m is its successor.


> node-sass@4.9.4 postinstall /home/nasiruddin/Desktop/Oct-10/MaterialSupportFeatureRequest/node_modules/node-sass
> node scripts/build.js

Binary found at /home/nasiruddin/Desktop/Oct-10/MaterialSupportFeatureRequest/node_modules/node-sass/vendor/linux-x64-64/binding.node
Testing binary
Binary is fine
npm notice created a lockfile as package-lock.json. You should commit this file.
npm WARN @ionic/angular-toolkit@1.0.0 requires a peer of @angular-devkit/architect@0.9.0-beta.3 but none is installed. You must install peer dependencies yourself.
npm WARN @ionic/angular-toolkit@1.0.0 requires a peer of @angular-devkit/build-angular@0.9.0-beta.3 but none is installed. You must install peer dependencies yourself.
npm WARN @ionic/angular-toolkit@1.0.0 requires a peer of @angular-devkit/core@0.9.0-beta.3 but none is installed. You must install peer dependencies yourself.
npm WARN @ionic/angular-toolkit@1.0.0 requires a peer of @angular-devkit/schematics@0.9.0-beta.3 but none is installed. You must install peer dependencies yourself.
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.4 (node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.4: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})

added 1083 packages from 1331 contributors and audited 49664 packages in 51.696s
found 0 vulnerabilities

> git init
Initialized empty Git repository in /home/nasiruddin/Desktop/Oct-10/MaterialSupportFeatureRequest/.git/

     🔥   IONIC  PRO   🔥

 Supercharge your Ionic development with the Ionic Pro SDK

  -  ⚠️   Track runtime errors in real-time, back to your original TypeScript
  -  📲  Push remote updates and skip the app store queue

 Learn more about Ionic Pro: https://ionicframework.com/pro

────────────────────────────────────────────────────────────

? Install the free Ionic Pro SDK and connect your app? No
> git add -A
> git commit -m "Initial commit" --no-gpg-sign
[master (root-commit) 201529b] Initial commit
 87 files changed, 11441 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 angular.json
 create mode 100644 config.xml
 create mode 100644 e2e/protractor.conf.js
 create mode 100644 e2e/src/app.e2e-spec.ts
 create mode 100644 e2e/src/app.po.ts
 create mode 100644 e2e/tsconfig.e2e.json
 create mode 100644 ionic.config.json
 create mode 100644 package-lock.json
 create mode 100644 package.json
 create mode 100644 resources/README.md
 create mode 100644 resources/android/icon/drawable-hdpi-icon.png
 create mode 100644 resources/android/icon/drawable-ldpi-icon.png
 create mode 100644 resources/android/icon/drawable-mdpi-icon.png
 create mode 100644 resources/android/icon/drawable-xhdpi-icon.png
 create mode 100644 resources/android/icon/drawable-xxhdpi-icon.png
 create mode 100644 resources/android/icon/drawable-xxxhdpi-icon.png
 create mode 100644 resources/android/splash/drawable-land-hdpi-screen.png
 create mode 100644 resources/android/splash/drawable-land-ldpi-screen.png
 create mode 100644 resources/android/splash/drawable-land-mdpi-screen.png
 create mode 100644 resources/android/splash/drawable-land-xhdpi-screen.png
 create mode 100644 resources/android/splash/drawable-land-xxhdpi-screen.png
 create mode 100644 resources/android/splash/drawable-land-xxxhdpi-screen.png
 create mode 100644 resources/android/splash/drawable-port-hdpi-screen.png
 create mode 100644 resources/android/splash/drawable-port-ldpi-screen.png
 create mode 100644 resources/android/splash/drawable-port-mdpi-screen.png
 create mode 100644 resources/android/splash/drawable-port-xhdpi-screen.png
 create mode 100644 resources/android/splash/drawable-port-xxhdpi-screen.png
 create mode 100644 resources/android/splash/drawable-port-xxxhdpi-screen.png
 create mode 100644 resources/icon.png
 create mode 100644 resources/ios/icon/icon-1024.png
 create mode 100644 resources/ios/icon/icon-40.png
 create mode 100644 resources/ios/icon/icon-40@2x.png
 create mode 100644 resources/ios/icon/icon-40@3x.png
 create mode 100644 resources/ios/icon/icon-50.png
 create mode 100644 resources/ios/icon/icon-50@2x.png
 create mode 100644 resources/ios/icon/icon-60.png
 create mode 100644 resources/ios/icon/icon-60@2x.png
 create mode 100644 resources/ios/icon/icon-60@3x.png
 create mode 100644 resources/ios/icon/icon-72.png
 create mode 100644 resources/ios/icon/icon-72@2x.png
 create mode 100644 resources/ios/icon/icon-76.png
 create mode 100644 resources/ios/icon/icon-76@2x.png
 create mode 100644 resources/ios/icon/icon-83.5@2x.png
 create mode 100644 resources/ios/icon/icon-small.png
 create mode 100644 resources/ios/icon/icon-small@2x.png
 create mode 100644 resources/ios/icon/icon-small@3x.png
 create mode 100644 resources/ios/icon/icon.png
 create mode 100644 resources/ios/icon/icon@2x.png
 create mode 100644 resources/ios/splash/Default-568h@2x~iphone.png
 create mode 100644 resources/ios/splash/Default-667h.png
 create mode 100644 resources/ios/splash/Default-736h.png
 create mode 100644 resources/ios/splash/Default-Landscape-736h.png
 create mode 100644 resources/ios/splash/Default-Landscape@2x~ipad.png
 create mode 100644 resources/ios/splash/Default-Landscape@~ipadpro.png
 create mode 100644 resources/ios/splash/Default-Landscape~ipad.png
 create mode 100644 resources/ios/splash/Default-Portrait@2x~ipad.png
 create mode 100644 resources/ios/splash/Default-Portrait@~ipadpro.png
 create mode 100644 resources/ios/splash/Default-Portrait~ipad.png
 create mode 100644 resources/ios/splash/Default@2x~iphone.png
 create mode 100644 resources/ios/splash/Default@2x~universal~anyany.png
 create mode 100644 resources/ios/splash/Default~iphone.png
 create mode 100644 resources/splash.png
 create mode 100644 src/app/app-routing.module.ts
 create mode 100644 src/app/app.component.html
 create mode 100644 src/app/app.component.spec.ts
 create mode 100644 src/app/app.component.ts
 create mode 100644 src/app/app.module.ts
 create mode 100644 src/app/home/home.module.ts
 create mode 100644 src/app/home/home.page.html
 create mode 100644 src/app/home/home.page.scss
 create mode 100644 src/app/home/home.page.spec.ts
 create mode 100644 src/app/home/home.page.ts
 create mode 100644 src/assets/icon/favicon.png
 create mode 100644 src/environments/environment.prod.ts
 create mode 100644 src/environments/environment.ts
 create mode 100644 src/global.scss
 create mode 100644 src/index.html
 create mode 100644 src/karma.conf.js
 create mode 100644 src/main.ts
 create mode 100644 src/polyfills.ts
 create mode 100644 src/test.ts
 create mode 100644 src/theme/variables.scss
 create mode 100644 src/tsconfig.app.json
 create mode 100644 src/tsconfig.spec.json
 create mode 100644 tsconfig.json
 create mode 100644 tslint.json

[INFO] Next Steps:
       
       - Go to your newly created project: cd ./MaterialSupportFeatureRequest
       - Get Ionic DevApp for easy device testing: https://bit.ly/ionic-dev-app


   ╭─────────────────────────────────────╮
   │                                     │
   │   Update available 4.1.2 → 4.2.1    │
   │    Run npm i -g ionic to update     │
   │                                     │
   ╰─────────────────────────────────────╯

nasiruddin@nasiruddin-PC:~/Desktop/Oct-10$ ^C
nasiruddin@nasiruddin-PC:~/Desktop/Oct-10$ cd MaterialSupportFeatureRequest/
nasiruddin@nasiruddin-PC:~/Desktop/Oct-10/MaterialSupportFeatureRequest$ ng add @angular/material
Installing packages for tooling via npm.
npm WARN @ionic/angular-toolkit@1.0.0 requires a peer of @angular-devkit/architect@0.9.0-beta.3 but none is installed. You must install peer dependencies yourself.
npm WARN @ionic/angular-toolkit@1.0.0 requires a peer of @angular-devkit/build-angular@0.9.0-beta.3 but none is installed. You must install peer dependencies yourself.
npm WARN @ionic/angular-toolkit@1.0.0 requires a peer of @angular-devkit/core@0.9.0-beta.3 but none is installed. You must install peer dependencies yourself.
npm WARN @ionic/angular-toolkit@1.0.0 requires a peer of @angular-devkit/schematics@0.9.0-beta.3 but none is installed. You must install peer dependencies yourself.
npm WARN @angular/material@6.4.7 requires a peer of @angular/cdk@6.4.7 but none is installed. You must install peer dependencies yourself.
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.4 (node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.4: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})

+ @angular/material@6.4.7
added 2 packages from 1 contributor and audited 49667 packages in 15.04s
found 0 vulnerabilities

Installed packages for tooling via npm.
UPDATE package.json (1860 bytes)
UPDATE angular.json (5246 bytes)
UPDATE src/app/app.module.ts (868 bytes)
UPDATE src/index.html (845 bytes)
UPDATE node_modules/@angular/material/prebuilt-themes/indigo-pink.css (58378 bytes)
npm WARN @ionic/angular-toolkit@1.0.0 requires a peer of @angular-devkit/architect@0.9.0-beta.3 but none is installed. You must install peer dependencies yourself.
npm WARN @ionic/angular-toolkit@1.0.0 requires a peer of @angular-devkit/build-angular@0.9.0-beta.3 but none is installed. You must install peer dependencies yourself.
npm WARN @ionic/angular-toolkit@1.0.0 requires a peer of @angular-devkit/core@0.9.0-beta.3 but none is installed. You must install peer dependencies yourself.
npm WARN @ionic/angular-toolkit@1.0.0 requires a peer of @angular-devkit/schematics@0.9.0-beta.3 but none is installed. You must install peer dependencies yourself.
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.4 (node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.4: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})

added 2 packages from 1 contributor and audited 49671 packages in 12.379s
found 0 vulnerabilities

nasiruddin@nasiruddin-PC:~/Desktop/Oct-10/MaterialSupportFeatureRequest$ ng generate @angular/material:material-nav --name shared/components/layout
CREATE src/app/shared/components/layout/layout.component.css (129 bytes)
CREATE src/app/shared/components/layout/layout.component.html (946 bytes)
CREATE src/app/shared/components/layout/layout.component.spec.ts (705 bytes)
CREATE src/app/shared/components/layout/layout.component.ts (599 bytes)
UPDATE src/app/app.module.ts (1232 bytes)
nasiruddin@nasiruddin-PC:~/Desktop/Oct-10/MaterialSupportFeatureRequest$  ng generate @angular/material:material-dashboard --name components/dashboardCREATE src/app/components/dashboard/dashboard.component.css (254 bytes)
CREATE src/app/components/dashboard/dashboard.component.html (935 bytes)
CREATE src/app/components/dashboard/dashboard.component.spec.ts (632 bytes)
CREATE src/app/components/dashboard/dashboard.component.ts (1066 bytes)
UPDATE src/app/app.module.ts (1431 bytes)
```