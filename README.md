# `@codexporer.io/expo-checkbox`

A theme-integrated checkbox component for Expo and React Native applications. Supports boolean or tri-state statuses (`checked`, `unchecked`, `indeterminate`), inline labels, customizable icons, and dynamic colors via `@codexporer.io/expo-app-theme`.

## Installation & Peer Dependencies

```bash
yarn add @codexporer.io/expo-checkbox
```

Ensure peer dependencies are installed:
```bash
yarn add @expo/vector-icons @codexporer.io/expo-app-theme
```

## Quick Start

### Basic Boolean Checkbox

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
import React, { useState } from 'react';
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

## Props Reference

| Prop | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `checked` | `boolean` | `false` | Simple boolean checked state |
| `status` | `'checked' \| 'unchecked' \| 'indeterminate'` | — | Tri-state status override |
| `label` | `string \| ReactNode` | — | Text label or custom node rendered next to the checkbox |
| `labelStyle` | `StyleProp<TextStyle>` | — | Custom text style for the label |
| `onPress` | `() => void` | — | Callback invoked when tapped |
| `color` | `string` | `theme.primary` | Active / checked icon color |
| `uncheckedColor` | `string` | `theme.border` | Inactive icon color |
| `size` | `number` | `24` | Icon size in points |
| `disabled` | `boolean` | `false` | Disables press interactions |
| `style` | `StyleProp<ViewStyle>` | — | Container style |

## License

MIT