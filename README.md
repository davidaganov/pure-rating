# Pure Rating

## Examples

- [GitHub](https://github.com/davidaganov21/pure-rating)
- [CodeSandbox](https://codesandbox.io/s/pure-rating-y5f1c7)

## Install

#### NPM / Yarn

```
git clone https://github.com/davidaganov21/pure-rating
cd pure-rating
npm install
```

## Usage

Simply use it like so:

```html
<RatingSelect name="example" :color="customColor" :size="25" :grade="5" :maxStars="5" @rating="value = $event"/>
```

## Style

By passing your class to the name parameter, you will set custom classes for the rating structure, you can refer to them like this:

````css
.custom-class__rating-select {
  ...
}
.custom-class__rating-list {
  ...
}
.custom-class__rating-star {
  ...
}
````

## Props

- `grade: Number` - default rating
- `maxStars: Number` - number of stars
- `size: Number` - the size of the stars
- `name: String` - set custom classes
- `color: Object` - custom colors (empty, star, hover, focus)

## Credits

Author: [David Aganov](https://github.com/davidaganov21)
