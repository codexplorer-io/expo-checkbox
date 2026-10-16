# AGENTS.md — `@codexporer.io/expo-checkbox`

## Package Overview
Theme-aware checkbox component for Expo and React Native. Supports boolean or tri-state statuses (`checked`, `unchecked`, `indeterminate`), inline labels, customizable icons, and dynamic colors via `@codexporer.io/expo-app-theme`.

## Peer Dependencies
All peer dependencies must be installed in consuming projects:
- `react`: `*`
- `react-native`: `*`
- `@expo/vector-icons`: `*`
- `@codexporer.io/expo-app-theme`: `*`

## Key Exports
- `Checkbox` (also `default` export): Interactive checkbox component.
- `CheckboxProps`: TypeScript interface for component properties.

## Critical Guidelines for AI Agents
- **ThemeProvider Requirement**: `Checkbox` calls `useAppTheme()` to derive `theme.primary`, `theme.border`, and `theme.text`. It must always be mounted within a `<ThemeProvider>` from `@codexporer.io/expo-app-theme`.
- **Use `onPress` (NO `onChange` prop exists)**: There is NO `onChange` prop. Always use `onPress`:
  ```tsx
  <Checkbox checked={checked} onPress={() => setChecked(!checked)} />
  ```
- **Tri-State Status**: Use `status="checked" | "unchecked" | "indeterminate"`. When `status` is provided, it takes precedence over `checked`.
- **Built-In Label**: Pass `label="Label text"` or a custom `ReactNode` directly to `<Checkbox label="..." />`. The component automatically wraps the icon and label in a flex row (`gap: 8`), and clicking the label triggers `onPress`.
- **Color Overrides**:
  - `color`: Active/indeterminate icon tint (defaults to `theme.primary`).
  - `uncheckedColor`: Inactive/unchecked icon outline tint (defaults to `theme.border`).
  - Label text color automatically defaults to `theme.text` (overridable with `labelStyle`).
- **Icons & Hit Slop**: Renders `MaterialCommunityIcons` (`'checkbox-marked'`, `'minus-box'`, `'checkbox-blank-outline'`). Includes built-in `hitSlop={{ top: 8, bottom: 8, left: 8, right: 8 }}` and `activeOpacity={0.7}`.
