# The Palmer Group tsconfig

## Usage

```bash
yarn add tsconfig-palmerhq --dev
```

Then in your project's `tsconfig.json`:

```json
{
  "extends": "./node_modules/tsconfig-palmerhq/tsconfig.json"
}
```

## What's inside?

```json
{
  "compilerOptions": {
    "allowSyntheticDefaultImports": true,
    "allowUnreachableCode": false,
    "downlevelIteration": true,
    "forceConsistentCasingInFileNames": true,
    "jsx": "react",
    "noFallthroughCasesInSwitch": true,
    "noImplicitAny": true,
    "noImplicitReturns": true,
    "noImplicitThis": true,
    "noUnusedLocals": true,
    "pretty": true,
    "sourceMap": true,
    "strict": true,
    "strictNullChecks": true,
    "suppressImplicitAnyIndexErrors": true
  }
}
```