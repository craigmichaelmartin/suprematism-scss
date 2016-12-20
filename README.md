# suprematism-scss
This repo provides raw variables to be used in the suprematism component repositories

### Installation
```bash
npm i -S CINBCUniversal/suprematism-scss
```


### As relates to colors
- Setting raw color variables in this repository allow for them to be
  defined once and shared across all the suprematism component repositories.
- _Colors_ (eg, blue-light) and not _semantic names_ (eg, primary) are defined
  here, and so can be altered in necessary. Component repo's define semantic
  names on top of these colors.


### As relates to z-index
- There are two _types_ of z-index levels: regular and meta.
- The meta refers to a qualitaviely higher layer than where ui interaction
  usually occurs. They do not exist in the same realm as typical ui stacking.
  Examples of meta layers include popovers, tooltips, modals, dropdowns, etc.
  Meta levels _must_ be shared accross components and so must be defined here.
- Regular z-index levels could be defined in each component (there is no
  inherent reason the z-indexes used internally in components need to be
  parallel). However, rather than each component re-defining its own arbitrary
  levels, for convenience they are defined here. This saves re-typing, as well
  as offers familiarity when working across components.


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
