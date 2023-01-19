# prereqs

nodejs, [pnpm](https://pnpm.io/)

# repro

```
pnpm i
pnpm -r build
```

results in this error:

```
packages/consumer build$ webpack
│ asset main.js 5.15 KiB [emitted] (name: main)
│ asset index.d.ts 143 bytes [emitted]
│ ./src/index.ts 1.21 KiB [built] [code generated]
│ ../interface/dist/index.js 1.21 KiB [built] [code generated]
│ ERROR in ../interface/dist/index.js 19:18-38
│ Module not found: Error: Can't resolve 'interface' in '/home/pavel/work/fluence/webpack-repro/packages/interface/
│ resolve 'interface' in '/home/pavel/work/fluence/webpack-repro/packages/interface/dist'
│   Parsed request is a module
│   using description file: /home/pavel/work/fluence/webpack-repro/packages/interface/package.json (relative path:
│     Field 'browser' doesn't contain a valid alias configuration
│     resolve as module
│       /home/pavel/work/fluence/webpack-repro/packages/interface/dist/node_modules doesn't exist or is not a direc
│       looking for modules in /home/pavel/work/fluence/webpack-repro/packages/interface/node_modules
│         single file module
│           using description file: /home/pavel/work/fluence/webpack-repro/packages/interface/package.json (relativ
│             no extension
│               Field 'browser' doesn't contain a valid alias configuration
│               /home/pavel/work/fluence/webpack-repro/packages/interface/node_modules/interface doesn't exist
│             .tsx
│               Field 'browser' doesn't contain a valid alias configuration
│               /home/pavel/work/fluence/webpack-repro/packages/interface/node_modules/interface.tsx doesn't exist
│             .ts
│               Field 'browser' doesn't contain a valid alias configuration
│               /home/pavel/work/fluence/webpack-repro/packages/interface/node_modules/interface.ts doesn't exist
│             .js
│               Field 'browser' doesn't contain a valid alias configuration
│               /home/pavel/work/fluence/webpack-repro/packages/interface/node_modules/interface.js doesn't exist
│         /home/pavel/work/fluence/webpack-repro/packages/interface/node_modules/interface doesn't exist
│       /home/pavel/work/fluence/webpack-repro/packages/node_modules doesn't exist or is not a directory
│       looking for modules in /home/pavel/work/fluence/webpack-repro/node_modules
│         single file module
│           No description file found in /home/pavel/work/fluence/webpack-repro/node_modules or above
│           no extension
│             Field 'browser' doesn't contain a valid alias configuration
│             /home/pavel/work/fluence/webpack-repro/node_modules/interface doesn't exist
│           .tsx
│             Field 'browser' doesn't contain a valid alias configuration
│             /home/pavel/work/fluence/webpack-repro/node_modules/interface.tsx doesn't exist
│           .ts
│             Field 'browser' doesn't contain a valid alias configuration
│             /home/pavel/work/fluence/webpack-repro/node_modules/interface.ts doesn't exist
│           .js
│             Field 'browser' doesn't contain a valid alias configuration
│             /home/pavel/work/fluence/webpack-repro/node_modules/interface.js doesn't exist
│         /home/pavel/work/fluence/webpack-repro/node_modules/interface doesn't exist
│       /home/pavel/work/fluence/node_modules doesn't exist or is not a directory
│       /home/pavel/work/node_modules doesn't exist or is not a directory
│       /home/pavel/node_modules doesn't exist or is not a directory
│       /home/node_modules doesn't exist or is not a directory
│       /node_modules doesn't exist or is not a directory
│  @ ./src/index.ts 19:18-38
│ webpack 5.64.4 compiled with 1 error in 521 ms
└─ Failed in 801ms
```

if you build with `tsc` instead of webpack, everything works
