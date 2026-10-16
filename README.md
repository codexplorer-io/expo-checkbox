# `@codexporer.io/expo-checkbox`

A theme-integrated checkbox component for Expo and React Native applications. Supports boolean or tri-state statuses (`checked`, `unchecked`, `indeterminate`), inline labels, customizable icons, and dynamic colors via `@codexporer.io/expo-app-theme`.

---

## Peer Dependencies

All peer dependencies must be installed in consuming projects:
- `react`: `*`
- `react-native`: `*`
- `@expo/vector-icons`: `*`
- `@codexporer.io/expo-app-theme`: `*`

---

## Installation

```bash
yarn add @codexporer.io/expo-checkbox
```

---

## Theme Requirement

`Checkbox` calls `useAppTheme()` internally to resolve colors (`theme.primary` for active state, `theme.border` for inactive state, and `theme.text` for label). The consuming application must mount `<ThemeProvider>` from `@codexporer.io/expo-app-theme` higher in the component tree, or an error will be thrown.

---

## Quick Start

### Basic Boolean Checkbox with Label

```tsx
import React, { useState } from 'react';
import { Checkbox } from '@codexporer.io/expo-checkbox';

export function SimpleCheckbox() {
  const [checked, setChecked] = useState(false);

  return (
    <Checkbox
      checked={checked}
      onPress={() => setChecked(!checked)}
      label="Enable audio effects"
    />
  );
}
```

### Tri-State / Indeterminate Checkbox

```tsx
import React from 'react';
import { Checkbox } from '@codexporer.io/expo-checkbox';

export function SelectAllOptions({ allSelected, someSelected, onToggle }) {
  const status = allSelected ? 'checked' : someSelected ? 'indeterminate' : 'unchecked';

  return (
    <Checkbox
      status={status}
      onPress={onToggle}
      label="Select All Items"
    />
  );
}
```

---

## Icon & State Resolution

State and icons from `@expo/vector-icons` (`MaterialCommunityIcons`):
- `status === 'checked'` (or `!status && checked`): icon `'checkbox-marked'`, color: `color || theme.primary`
- `status === 'indeterminate'`: icon `'minus-box'`, color: `color || theme.primary`
- `status === 'unchecked'` (or `!status && !checked`): icon `'checkbox-blank-outline'`, color: `uncheckedColor || theme.border`

Touch area includes built-in `hitSlop={{ top: 8, bottom: 8, left: 8, right: 8 }}` and `activeOpacity={0.7}`.

---

## Props Reference

| Prop | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `checked` | `boolean` | `false` | Simple boolean checked state |
| `status` | `'checked' \| 'unchecked' \| 'indeterminate'` | — | Tri-state status (takes precedence over `checked`) |
| `label` | `string \| React.ReactNode` | — | Text label or custom node rendered next to the checkbox |
| `labelStyle` | `StyleProp<TextStyle>` | — | Custom text style for the label (default: `fontSize: 16`, `color: theme.text`) |
| `onPress` | `() => void` | — | Tap callback handler for the checkbox row |
| `color` | `string` | `theme.primary` | Active / checked icon color |
| `uncheckedColor` | `string` | `theme.border` | Inactive / unchecked outline icon color |
| `size` | `number` | `24` | Icon diameter in points |
| `disabled` | `boolean` | `false` | Disables touch interaction |
| `style` | `StyleProp<ViewStyle>` | — | Outer container style override |

---

## License

MIT