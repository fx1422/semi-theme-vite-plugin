# semi-theme-vite-plugin

A Vite plugin for Semi Design theme customization, supporting dynamic theme
switching and SCSS compilation.

## Features

- 🎨 Dynamic Semi Design theme switching
- 📦 Support for all package managers (npm, yarn, pnpm)
- 🔧 Custom variables and prefix class support
- 🚀 Optimized for Vite build process
- 📝 Full TypeScript support

## Installation

```bash
# npm
npm install semi-theme-vite-plugin --save-dev

# yarn
yarn add semi-theme-vite-plugin --dev

# pnpm
pnpm add semi-theme-vite-plugin --save-dev
```

## Usage

### Basic Usage

```typescript
// vite.config.ts
import { defineConfig } from 'vite';
import SemiPlugin from 'semi-theme-vite-plugin';

export default defineConfig({
  plugins: [
    SemiPlugin({
      theme: '@semi-bot/semi-theme-XXX',
    }),
  ],
});
```

### Advanced Configuration

```typescript
// vite.config.ts
import { defineConfig } from 'vite';
import SemiPlugin from 'semi-theme-vite-plugin';

export default defineConfig({
  plugins: [
    SemiPlugin({
      theme: '@semi-bot/semi-theme-XXX',
      options: {
        prefixCls: 'my-semi',
        variables: {
          '--semi-color-primary': '#1890ff',
          '--semi-color-secondary': '#52c41a',
        },
        include: './src/styles/custom-variables.scss',
      },
    }),
  ],
});
```

## API

### SemiPluginOptions

| Property            | Type                               | Default  | Description                    |
| ------------------- | ---------------------------------- | -------- | ------------------------------ |
| `theme`             | `string`                           | -        | Semi Design theme package name |
| `options.prefixCls` | `string`                           | `'semi'` | CSS class prefix               |
| `options.variables` | `Record<string, string \| number>` | `{}`     | Custom CSS variables           |
| `options.include`   | `string`                           | -        | Path to additional SCSS file   |

## Package Manager Support

This plugin supports all major package managers:

- ✅ **npm** - Full support
- ✅ **yarn** - Full support
- ✅ **pnpm** - Full support (with hoisting)

The plugin uses file system-level resolution that works across different package
managers by:

1. Recursively searching for `node_modules` directories
2. Supporting both flat and nested dependency structures
3. Handling symbolic links used by pnpm

## How It Works

1. **CSS to SCSS Conversion**: Intercepts Semi Design CSS imports and converts
   them to SCSS
2. **Theme Injection**: Injects theme variables and imports into SCSS files
3. **Dynamic Compilation**: Compiles SCSS with custom variables and theme
   settings
4. **Path Resolution**: Resolves `~` imports to `node_modules` packages

## License

MIT

## Contributing

Contributions are welcome! Please read our contributing guidelines before
submitting PRs.

## Related

- [Semi Design](https://semi.design/)
- [Vite](https://vitejs.dev/)
- [Semi Design Webpack Plugin](https://github.com/DouyinFE/semi-design/tree/main/packages/semi-webpack)
