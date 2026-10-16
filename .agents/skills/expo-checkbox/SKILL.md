---
name: expo-checkbox
description: Instructions and guidelines for using @codexporer.io/expo-checkbox (Expo Checkbox) in React Native and Expo applications.
---

# `@codexporer.io/expo-checkbox` Skill

## Overview
`@codexporer.io/expo-checkbox` provides a theme-integrated checkbox component for Expo and React Native. Supports boolean or tri-state statuses (`checked`, `unchecked`, `indeterminate`), inline labels, customizable icons, and dynamic colors via `@codexporer.io/expo-app-theme`.

---

## Peer Dependencies

All peer dependencies must be installed in consuming projects:
- `react`: `*`
- `react-native`: `*`
- `@expo/vector-icons`: `*`
- `@codexporer.io/expo-app-theme`: `*`

---

## Theme Requirement

`Checkbox` calls `useAppTheme()` internally to resolve colors (`theme.primary`, `theme.border`, and `theme.text`). The consuming application must mount `<ThemeProvider>` from `@codexporer.io/expo-app-theme` higher in the component tree.

---

## When to Use
- Multi-selection lists (e.g., selecting items or assets).
- Form agreement checkboxes (terms of service, opt-in settings).
- Tri-state "select all" toggles.

---

## Usage Example

### Basic Checkbox with Inline Label

```tsx
import React, { useState } from 'react';
import { View } from 'react-native';
import { Checkbox } from '@codexporer.io/expo-checkbox';

export function AgreeCheckboxRow() {
  const [agreed, setAgreed] = useState(false);

  return (
    <View style={{ padding: 16 }}>
      <Checkbox
        checked={agreed}
        onPress={() => setAgreed(!agreed)}
        label="I accept the terms and conditions"
      />
    </View>
  );
}
```

### Tri-State "Select All" Checkbox

```tsx
import React from 'react';
import { Checkbox } from '@codexporer.io/expo-checkbox';

export function SelectAllRow({ allSelected, someSelected, onToggle }) {
  const status = allSelected ? 'checked' : someSelected ? 'indeterminate' : 'unchecked';

  return (
    <Checkbox
      status={status}
      onPress={onToggle}
      label="Select All"
    />
  );
}
```

---

## API Reference

### `<Checkbox />` Props

| Prop | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `checked` | `boolean` | `false` | Simple boolean checked state |
| `status` | `'checked' \| 'unchecked' \| 'indeterminate'` | — | Tri-state status override (takes precedence over `checked`) |
| `label` | `string \| React.ReactNode` | — | Text label or custom ReactNode rendered beside checkbox |
| `labelStyle` | `StyleProp<TextStyle>` | — | Custom text style for the label |
| `onPress` | `() => void` | — | Tap callback handler for the checkbox and label |
| `color` | `string` | `theme.primary` | Active / indeterminate icon tint |
| `uncheckedColor` | `string` | `theme.border` | Inactive / unchecked outline icon tint |
| `size` | `number` | `24` | Icon diameter in points |
| `disabled` | `boolean` | `false` | Disables touch interactions |
| `style` | `StyleProp<ViewStyle>` | — | Outer container style override |

---

## Critical Rules & Guidelines
1. **ThemeProvider Requirement**: `Checkbox` calls `useAppTheme()` and must be mounted within `<ThemeProvider>`.
2. **Use `onPress`, Not `onChange`**: There is NO `onChange` prop on `Checkbox`. Bind state updates using `onPress={() => setChecked(!checked)}`.
3. **Use Built-In `label`**: Pass labels directly via `label="..."`. The component automatically structures the icon and label in a row (`gap: 8`), and clicking the label triggers `onPress`. Do not wrap in an unnecessary outer `TouchableOpacity`.
4. **Hit Slop Included**: `Checkbox` includes built-in `hitSlop={{ top: 8, bottom: 8, left: 8, right: 8 }}` and `activeOpacity={0.7}`.
