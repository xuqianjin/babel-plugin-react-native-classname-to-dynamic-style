# babel-plugin-react-native-classname-to-dynamic-style-extend

Transform JSX `className` property to a `style` property that calculates styles at runtime in React Native. The plugin is used to match style objects containing parsed CSS media queries and CSS viewport units with React Native.

## Usage

### Step 1: Install

```sh
yarn add --dev babel-plugin-react-native-classname-to-dynamic-style-extend
```

or

```sh
npm install --save-dev babel-plugin-react-native-classname-to-dynamic-style-extend
```

### Step 2: Configure `.babelrc`

```
{
  "presets": [
    "react-native"
  ],
  "plugins": [
    "react-native-classname-to-dynamic-style-extend"
  ]
}
```

## Syntax

## Single class

Example:

```jsx
<Text className={styles.myClass} />
```

↓ ↓ ↓ ↓ ↓ ↓

```jsx
var _reactNativeDynamicStyleProcessor = require("react-native-dynamic-style-processor");

<Text style={_reactNativeDynamicStyleProcessor.process(styles).myClass} />;
```

```jsx
<Text className={isTrue && styles.myClass} />
```

↓ ↓ ↓ ↓ ↓ ↓

```jsx
var _reactNativeDynamicStyleProcessor = require("react-native-dynamic-style-processor");

<Text
  style={isTrue && _reactNativeDynamicStyleProcessor.process(styles).myClass}
/>;
```

---

...or with `className` and `style`:

```jsx
<Text className={styles.myClass} style={{ color: "blue" }} />
```

↓ ↓ ↓ ↓ ↓ ↓

```jsx
var _reactNativeDynamicStyleProcessor = require("react-native-dynamic-style-processor");

<Text
  style={[
    _reactNativeDynamicStyleProcessor.process(styles).myClass,
    { color: "blue" }
  ]}
/>;
```

## Multiple classes

#### Using `[styles.class1, styles.class2].join(" ")` syntax

Example:

```jsx
<Text className={[styles.class1, styles.class2].join(" ")} />
```

↓ ↓ ↓ ↓ ↓ ↓

```jsx
var _reactNativeDynamicStyleProcessor = require("react-native-dynamic-style-processor");

<Text
  style={[
    _reactNativeDynamicStyleProcessor.process(styles).class1,
    _reactNativeDynamicStyleProcessor.process(styles).class2
  ]}
/>;
```

---

...or with `className` and `style`:

```jsx
<Text
  className={[styles.class1, styles.class2].join(" ")}
  style={{ color: "blue" }}
/>
```

↓ ↓ ↓ ↓ ↓ ↓

```jsx
var _reactNativeDynamicStyleProcessor = require("react-native-dynamic-style-processor");

<Text
  style={[
    _reactNativeDynamicStyleProcessor.process(styles).class1,
    _reactNativeDynamicStyleProcessor.process(styles).class2,
    { color: "blue" }
  ]}
/>;
```

#### Using template literal syntax

Example:

```jsx
<Text className={`${styles.class1} ${styles.class2}`} />
```

↓ ↓ ↓ ↓ ↓ ↓

```jsx
var _reactNativeDynamicStyleProcessor = require("react-native-dynamic-style-processor");

<Text
  style={[
    _reactNativeDynamicStyleProcessor.process(styles).class1,
    _reactNativeDynamicStyleProcessor.process(styles).class2
  ]}
/>;
```

---

...or with `className` and `style`:

```jsx
<Text
  className={`${styles.class1} ${styles.class2}`}
  style={{ color: "blue" }}
/>
```

↓ ↓ ↓ ↓ ↓ ↓

```jsx
var _reactNativeDynamicStyleProcessor = require("react-native-dynamic-style-processor");

<Text
  style={[
    _reactNativeDynamicStyleProcessor.process(styles).class1,
    _reactNativeDynamicStyleProcessor.process(styles).class2,
    { color: "blue" }
  ]}
/>;
```

## Using ternary operator

Example:

```jsx
<Text className={isTrue ? styles.class1 : styles.class2} />
```

↓ ↓ ↓ ↓ ↓ ↓

```jsx
var _reactNativeDynamicStyleProcessor = require("react-native-dynamic-style-processor");

<Text
  style={
    isTrue
      ? _reactNativeDynamicStyleProcessor.process(styles).class1
      : _reactNativeDynamicStyleProcessor.process(styles).class2
  }
/>;
```

#### Using array

Example:

```jsx
<Text className={[styles.class1, styles.class2]} />
```

↓ ↓ ↓ ↓ ↓ ↓

```jsx
var _reactNativeDynamicStyleProcessor = require("react-native-dynamic-style-processor");

<Text
  style={[
    _reactNativeDynamicStyleProcessor.process(styles).class1,
    _reactNativeDynamicStyleProcessor.process(styles).class2
  ]}
/>;
```

#### Using array operator

Example:

```jsx
<Text className={[styles.class1, isTrue && styles.class2]} />
```

↓ ↓ ↓ ↓ ↓ ↓

```jsx
var _reactNativeDynamicStyleProcessor = require("react-native-dynamic-style-processor");

<Text
  style={[
    _reactNativeDynamicStyleProcessor.process(styles).class1,
    isTrue && _reactNativeDynamicStyleProcessor.process(styles).class2
  ]}
/>;
```

```jsx
<Text className={[styles.class1, isTrue ? styles.class2 : styles.class3]} />
```

↓ ↓ ↓ ↓ ↓ ↓

```jsx
var _reactNativeDynamicStyleProcessor = require("react-native-dynamic-style-processor");

<Text
  style={[
    _reactNativeDynamicStyleProcessor.process(styles).class1,
    isTrue
      ? _reactNativeDynamicStyleProcessor.process(styles).class2
      : _reactNativeDynamicStyleProcessor.process(styles).class3
  ]}
/>;
```
