---
name: expo-checkbox
description: Instructions and guidelines for using @codexporer.io/expo-checkbox (Expo Checkbox) in React Native and Expo applications.
---

# `@codexporer.io/expo-checkbox` Skill

## Overview
`@codexporer.io/expo-checkbox` provides a theme-integrated binary selection toggle component supporting custom sizes, disabled states, and dynamic colors derived from `@codexporer.io/expo-app-theme`.

---

## When to Use
- Multi-selection lists (e.g., selecting multiple photos or project assets).
- Form agreement checkboxes (terms of service, opt-in settings).
- Toggle switches in modal options.

---

## Usage Example

```tsx
import React, { useState } from 'react';
import { View, Text, TouchableOpacity } from 'react-native';
import { Checkbox } from '@codexporer.io/expo-checkbox';

export function AgreeCheckboxRow() {
  const [agreed, setAgreed] = useState(false);

  return (
    <TouchableOpacity
      activeOpacity={0.8}
      onPress={() => setAgreed(!agreed)}
      style={{ flexDirection: 'row', alignItems: 'center', gap: 12 }}
    >
      <Checkbox checked={agreed} onChange={setAgreed} />
      <Text>I accept the terms and conditions</Text>
    </TouchableOpacity>
  );
}
```

---

## API Reference

### `<Checkbox />` Props

| Prop | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `checked` | `boolean` | `false` | Controlled checked state |
| `onChange` | `(checked: boolean) => void` | — | Callback invoked with next boolean state |
| `disabled` | `boolean` | `false` | Disables interaction and reduces opacity |
| `size` | `number` | `24` | Dimension of checkbox square in points |
| `checkmarkColor` | `string` | `theme.background` | Color of inner checkmark check icon |
| `checkedColor` | `string` | `theme.primary` | Background fill when checked |
| `uncheckedColor` | `string` | `theme.border` | Border stroke color when unchecked |
| `style` | `StyleProp<ViewStyle>` | — | Outer container style override |

---

## Critical Rules & Guidelines
1. **Row Tap Convenience**: Wrap the checkbox and label in a `TouchableOpacity` or `Pressable` with `onPress={() => setChecked(!checked)}` so users can tap anywhere on the label to toggle.
2. **Colors Automatically Dynamic**: Do not hardcode `checkedColor` unless specific non-theme branding is explicitly needed.
