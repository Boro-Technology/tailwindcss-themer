# Migrating to Tailwind CSS v4

This guide helps you migrate `tailwindcss-themer` from Tailwind CSS v3 to v4.

## Overview

The `tailwindcss-themer` plugin has been updated to support Tailwind CSS v4.0+. The plugin API remains the same for end users, so your configuration should continue to work without changes.

## Requirements

- Tailwind CSS v4.0.0 or higher
- Updated `tailwindcss-themer` package

## Installation

Update your dependencies:

```bash
npm install --save-dev tailwindcss@^4.0.0 tailwindcss-themer@latest
```

or with yarn:

```bash
yarn add --dev tailwindcss@^4.0.0 tailwindcss-themer@latest
```

## Configuration

The plugin configuration remains the same. Your existing `tailwind.config.js` should work without modifications:

```js
// tailwind.config.js
module.exports = {
  plugins: [
    require('tailwindcss-themer')({
      defaultTheme: {
        extend: {
          colors: {
            primary: 'red'
          }
        }
      },
      themes: [
        {
          name: 'my-theme',
          extend: {
            colors: {
              primary: 'blue'
            }
          }
        }
      ]
    })
  ]
}
```

## What Changed

### Internal Changes

The plugin has been refactored internally to work with Tailwind CSS v4's new plugin API:

1. **Removed `plugin.withOptions()`**: The plugin now uses the standard `plugin()` function with options passed directly
2. **Removed `e()` escape function**: Now uses a custom escape function compatible with Tailwind v4
3. **Updated type definitions**: Uses Tailwind v4's updated type definitions

### User-Facing Changes

**No breaking changes** - The plugin API remains the same. Your existing configuration will work as-is.

## Tailwind CSS v4 Features

If you're migrating your entire project to Tailwind CSS v4, you may want to take advantage of new features:

### CSS-First Configuration

Tailwind v4 supports CSS-first configuration using the `@theme` directive. However, `tailwindcss-themer` continues to work with JavaScript configuration files, so you don't need to migrate your theme configuration to CSS unless you want to.

### New Plugin System

The plugin system in Tailwind v4 has been streamlined, but `tailwindcss-themer` handles these changes internally, so you don't need to change how you use the plugin.

## Troubleshooting

### Plugin Not Working

If the plugin doesn't seem to be working:

1. Verify you have Tailwind CSS v4.0.0 or higher installed
2. Check that `tailwindcss-themer` is the latest version
3. Ensure your `tailwind.config.js` is properly configured
4. Check the browser console for any CSS variable errors

### Type Errors

If you encounter TypeScript errors:

1. Make sure you have the latest `@types/tailwindcss` or Tailwind v4 types
2. Update your TypeScript version if needed
3. Clear your TypeScript cache and restart your IDE

### CSS Variables Not Generated

If CSS variables aren't being generated:

1. Verify your theme configuration is correct
2. Check that your content paths in `tailwind.config.js` include all files using the themed classes
3. Ensure you're applying theme classes correctly (e.g., `class="my-theme"`)

## Backward Compatibility

This version of `tailwindcss-themer` is **not** backward compatible with Tailwind CSS v3. If you need to use Tailwind v3, please use an earlier version of this plugin.

## Need Help?

If you encounter issues during migration:

1. Check the [Common Problems](./README.md#common-problems) section
2. Review the [Config Documentation](./config.md)
3. Open an issue on GitHub with details about your setup and the problem you're experiencing

## Examples

All example projects have been updated to work with Tailwind CSS v4. See the [examples directory](../examples/) for reference implementations.
