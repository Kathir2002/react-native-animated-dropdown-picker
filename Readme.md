# react-native-animated-dropdown-picker

A highly customizable, animated dropdown picker for React Native with support for single and multiple selection, search functionality, and extensive styling options.

## Features

- 🎨 Fully customizable styling
- 🔍 Search functionality
- 🔢 Single and multiple selection modes
- 📱 Responsive design
- 🌈 Animated interactions
- 🏷️ Supports nested items and categories
- 🎭 Customizable icons and components

## Installation

Install the package using npm or yarn:

```bash
npm install react-native-animated-dropdown-picker
# or
yarn add react-native-animated-dropdown-picker
```

## Basic Usage

```jsx
import React, { useState } from "react";
import { View } from "react-native";
import { AnimatedDropdown } from "react-native-animated-dropdown-picker";

const App = () => {
  const [open, setOpen] = useState(false);
  const [value, setValue] = useState(null);

  const items = [
    { label: "Apple", value: "apple" },
    { label: "Banana", value: "banana" },
    { label: "Orange", value: "orange" },
  ];

  return (
    <View>
      <AnimatedDropdown
        open={open}
        value={value}
        items={items}
        setOpen={setOpen}
        setValue={setValue}
        placeholder="Select an item"
      />
    </View>
  );
};

export default App;
```

## Props Overview

### Core Props

| Prop       | Type         | Required | Description                         | Default |
| ---------- | ------------ | -------- | ----------------------------------- | ------- |
| `items`    | `ItemType[]` | Yes      | Array of dropdown items             | `[]`    |
| `open`     | `boolean`    | Yes      | Dropdown open state                 | `false` |
| `setOpen`  | `function`   | Yes      | Function to set dropdown open state | -       |
| `value`    | `any`        | Yes      | Currently selected value            | `null`  |
| `setValue` | `function`   | Yes      | Function to update selected value   | -       |
| `multiple` | `boolean`    | No       | Enable multiple selection           | `false` |

### Item Type Structure

```typescript
interface ItemType<T> {
  label: string;
  value: T;
  parent?: string;
  selectable?: boolean;
  disabled?: boolean;
  containerStyle?: StyleProp<ViewStyle>;
  labelStyle?: StyleProp<TextStyle>;
  testID?: string;
  selected?: boolean;
}
```

## Detailed Props Reference

### Selection and Interaction Props

| Prop                  | Type       | Description                                                  | Default                 |
| --------------------- | ---------- | ------------------------------------------------------------ | ----------------------- |
| `onChangeValue`       | `function` | Callback when value changes                                  | -                       |
| `onSelectItem`        | `function` | Callback when an item is selected                            | -                       |
| `disabled`            | `boolean`  | Disable the entire dropdown                                  | `false`                 |
| `closeAfterSelecting` | `boolean`  | Close dropdown after item selection                          | `true`                  |
| `min`                 | `number`   | Minimum number of items that can be selected (multiple mode) | `null`                  |
| `max`                 | `number`   | Maximum number of items that can be selected (multiple mode) | `null`                  |
| `multipleText`        | `string`   | Custom text for multiple selection                           | "Selected Items Count:" |

### Search Props

| Prop                         | Type      | Description                       | Default                      |
| ---------------------------- | --------- | --------------------------------- | ---------------------------- |
| `searchable`                 | `boolean` | Enable search functionality       | `false`                      |
| `searchPlaceholder`          | `string`  | Placeholder text for search input | "Search"                     |
| `searchPlaceholderTextColor` | `string`  | Color of search placeholder       | `appColors.placeholderColor` |

### Styling Props

#### Container Styles

| Prop                     | Type                   | Description                            |
| ------------------------ | ---------------------- | -------------------------------------- |
| `containerStyle`         | `StyleProp<ViewStyle>` | Styles for the main dropdown container |
| `style`                  | `StyleProp<ViewStyle>` | Additional styles for dropdown         |
| `dropDownContainerStyle` | `StyleProp<ViewStyle>` | Styles for the dropdown list container |
| `disabledStyle`          | `StyleProp<ViewStyle>` | Styles when dropdown is disabled       |

#### Text Styles

| Prop               | Type                   | Description                    |
| ------------------ | ---------------------- | ------------------------------ |
| `textStyle`        | `StyleProp<TextStyle>` | Styles for dropdown text       |
| `labelStyle`       | `StyleProp<TextStyle>` | Styles for selected item label |
| `placeholderStyle` | `StyleProp<TextStyle>` | Styles for placeholder text    |

#### List Item Styles

| Prop                         | Type                   | Description                        |
| ---------------------------- | ---------------------- | ---------------------------------- |
| `listItemContainerStyle`     | `StyleProp<ViewStyle>` | Styles for list item container     |
| `listItemLabelStyle`         | `StyleProp<TextStyle>` | Styles for list item label         |
| `selectedItemContainerStyle` | `StyleProp<ViewStyle>` | Styles for selected item container |
| `selectedItemLabelStyle`     | `StyleProp<TextStyle>` | Styles for selected item label     |
| `disabledItemContainerStyle` | `StyleProp<ViewStyle>` | Styles for disabled item container |
| `disabledItemLabelStyle`     | `StyleProp<TextStyle>` | Styles for disabled item label     |

### Icon and Component Props

| Prop                     | Type       | Description                       | Default        |
| ------------------------ | ---------- | --------------------------------- | -------------- |
| `showTickIcon`           | `boolean`  | Show tick icon for selected items | `true`         |
| `TickIconComponent`      | `function` | Custom tick icon component        | Built-in image |
| `showArrowIcon`          | `boolean`  | Show dropdown arrow               | `true`         |
| `ArrowUpIconComponent`   | `function` | Custom up arrow icon              | Built-in image |
| `ArrowDownIconComponent` | `function` | Custom down arrow icon            | Built-in image |

### Advanced Props

| Prop                 | Type                | Description                            | Default            |
| -------------------- | ------------------- | -------------------------------------- | ------------------ |
| `maxHeight`          | `number`            | Maximum height of dropdown list        | `200`              |
| `zIndex`             | `number`            | Z-index of dropdown                    | `5000`             |
| `dropdownDirection`  | `"BOTTOM" \| "TOP"` | Direction dropdown opens               | `"BOTTOM"`         |
| `stickyHeader`       | `boolean`           | Enable sticky headers for parent items | `false`            |
| `categorySelectable` | `boolean`           | Allow selecting category items         | `true`             |
| `loading`            | `boolean`           | Show loading state                     | `false`            |
| `ListEmptyComponent` | `function`          | Custom component for empty list        | Built-in component |

## Customization Example

```jsx
<AnimatedDropdown
  multiple
  open={open}
  value={selectedValues}
  items={items}
  setOpen={setOpen}
  setValue={setSelectedValues}
  placeholder="Select multiple items"
  searchable
  min={1}
  max={3}
  searchPlaceholder="Search items..."
  containerStyle={customContainerStyle}
  dropDownContainerStyle={customDropdownStyle}
  onSelectItem={(selectedItems) => console.log(selectedItems)}
/>
```

## Color Theme

The package provides a default color palette:

```javascript
const appColors = {
  primary: "#7F3DFF",
  light: "#FFFFFF",
  dark: "#212325",
  formBorderColor: "#F1F1FA",
  placeholderColor: "#91919F",
};
```

## Performance Tips

- Use `memo` or `useMemo` for item lists to prevent unnecessary re-renders
- Keep the `items` array stable between renders
- Use `testID` for easier testing and debugging

## Author

Created with ❤️ by Kathir
