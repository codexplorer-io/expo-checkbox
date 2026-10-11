# AGENTS.md — `@codexporer.io/expo-checkbox`

## Package Overview
Theme-aware checkbox control with smooth checked/unchecked transition and accessibility compliance.

## Key Exports
- `Checkbox`: Interactive toggle checkbox component.
- `CheckboxProps`: Props interface.

## Critical Guidelines for AI Agents
- Bind `checked: boolean` and `onChange: (checked: boolean) => void`.
- Colors automatically default to `theme.primary` for checked background and `theme.border` for unchecked outline.
- Standard default size is `24` points. Avoid shrinking below `20` to maintain touch target usability.
