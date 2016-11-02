# suprematism-scss
This repo provides raw variables to be used in the suprematism component repositories

### Installation
```bash
npm i -S CINBCUniversal/suprematism-scss
```

### Rationale

- Setting raw color variables in this repository allow for them to be
  defined once and shared across all the suprematism component repositories.


### Define variable in this repo, or component repo?

- Values for variables that are inherently shareable should always be
  defined in this repository.
- Values for variables that are inherently bound to the component
  (ie, are inconceivable apart from the component) should be defined in
  the component repository.
- Rule of thumb: color, z-index, and rem values are usually inherently
  sharable; size properties using px can go either way; size properties
  using em are usually inherently component specific.


### Component Variable Usage

- Each component repo should set it's own variables for values, either derived
  from this repository, or literal values. (The global variables in this repo
  should not be used directly as css properties, but only as values for local
  variables in the component.)
- Preference should be given to css properties using variables
  and not literal values.


##### Example
```scss
// **suprematism-scss/_colors**

// Raw Colors
$blue-light: rba(...);
$red-dark: rba(...);

// Categories
$warning-color: $red-dark;
```
```scss
// **suprematism-awesome-components/src/awe.component.scss**

@import "suprematism-scss/colors"
$awe-text-color: $blue-light !default;
$awe-text-warning-color: $warning-color !default;
$awe-line-height: 1.1em !default;
```
