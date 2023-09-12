I have difficulty remembering how to get started with TypeScript.

Let's make a starter. I'm assuming you're using npm. I'm also assuming your using PowerShell on Windows 10/11.

(create a project directory)

1. mkdir typescript-starter && cd typescript-starter

(initialize a package.json configuration file) 2. npm init -y

(add TypeScript as a development dependency) 3. npm install typescript --save-dev

(add DefinitelyTyped type definition for Node, gives us ambient types) 4. npm install @types/node --save-dev

(create a basic tsconfig.json file for the TypeScript compiler) 5. npx tsc --init --rootDir src --outDir build \
--esModuleInterop --resolveJsonModule --lib es6 \
--module commonjs --allowJs true --noImplicitAny true

(make an index.ts entry point under src) 6. mkdir src && ni src/index.ts

(enable cold reloading for development) 7. npm install --save-dev ts-node nodemon

(add nodemon.json configuration file)

{
"watch": ["src"],
"ext": ".ts,.js",
"ignore": [],
"exec": "npx ts-node ./src/index.ts"
}

(add start up for nodemon to package.json) 8. add "start:dev": "npx nodemon" to the scripts entry

(add rimraf and a build script to clean and build for production) 9. npm install --save-dev rimraf and add to your pacakge.json, in the scripts section:

"build": "rimraf ./build && tsc",

This will clean out the build directory before the TypeScript compiler goes to work and emits freshly built JavaScript to the /dist folder.

(add a start script to package.json which runs our build script and starts our index.js entry point file) 10. add to your package.json: "start": "npm run build && node build/index.js"

Whew!

That's it! You can now develop something bigger in TypeScript.

You can make the above into a repo, save it on GitHub, then clone it locally to use it as a starting point for a new project.
