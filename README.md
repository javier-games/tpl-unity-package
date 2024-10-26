# Unity Packages Installation Methods

There are several ways to install a **Unity Package** into your Unity project with the [Unity Package Manager (UPM)](https://docs.unity3d.com/Manual/Packages.html). 
Choose the method that best fits your workflow. For easy updates and access to future releases, 
we recommend using a npm scoped registry.

## Scoped Registries Installation

If the package is distributed via a public npm registry it can be easily added using the Unity Editor or manually added to the `Packages/manifest.json`.
For the Package you want to install locate the following information that will be required by any of both methods.

- **Name**: Display name of the Package.
- **Scope**: Scope of the package(s), example: `my.scope`.
- **URL**: URL of the registry. 
  - For **npm**: `https://registry.npmjs.org`.
  - For **Open UPM**:`https://package.openupm.com`.
  - For **GitHub** registries please read this [thread](https://discussions.unity.com/t/using-github-packages-registry-with-unity-package-manager/784073).
  - For **GitLab** registries please read the [documentation](https://docs.gitlab.com/ee/user/packages/npm_registry/).

### Via Unity Editor

1. Open your Unity project and go to `Edit > Project Settings > Package Manager`.
2. In the `Scoped Registries` section, click the `+` button to add a new registry.
3. Fill in the fields with the Name, Scope and URL.
4. Click `Save`, then close the Project Settings window.
5. Open the Package Manager by navigating to `Window > Package Manager`.
6. In the Package Manager, select `Packages: My Registries` from the dropdown.
7. Find your package listed. Click `Install` to add it to your project.

### Via Manifest

You can also directly modify your `Packages/manifest.json` and `Packages/packages-lock.json` files with the Name, Scope and URL:

1. Add the scope entry to the `scopedRegistries` section of your `manifest.json`, example:
   ```json
   {
     "scopedRegistries": [
       {
         "name": "Package Name",
         "url": "https://registry",
         "scopes": ["my.scope"]
       }
     ]
   }
   ```
2. Add the package to the `dependencies` section, example:
   ```json
   {
     "dependencies": {
       "my.scope.package.name": "1.0.0"
     }
   }
   ```
   
## OpenUPM CLI Installation

If the package is available on OpenUPM it can be easily installed using the OpenUPM CLI. 
Make sure you have Node.js v16 or higher and the [openupm-cli](https://openupm.com/docs/getting-started-cli.html) installed.

Run the following command:

```bash
openupm add my.scope.package.name
```

## Cloning Installation

If the package is located in a git repository you clone it or added to your repository as a submodule under the Packages folder and Unity will recognize automatically the package. 
It can also be clone it outside of your project:

1. Clone the repository to your local machine.
2. Open Unity and go to `Window > Package Manager`.
3. Click the `+` button in the top-left corner, then select `Add package from disk...`.
4. In the file explorer, navigate to the cloned repository and select the `package.json` file.
5. Click `Open` to add the package to your project.

## Install from Git URL

If you prefer, you can directly install the package from the Git repository:

1. In Unity, go to `Window > Package Manager`.
2. Click the `+` button and select `Add package from git URL...`.
3. Enter the repository URL and press install.

Using this method will not show any updates or previous versions.

## Install from a Tarball

If you have access to the package Tarball..

1. In Unity, go to `Window > Package Manager`.
2. Click the `+` button and select `Add package from tarball...`.
3. Locate the downloaded tarball and click `Open`.
