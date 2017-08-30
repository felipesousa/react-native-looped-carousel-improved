# react-native-looped-carousel-improved
### Simple and Powerful Carousel to React Native.
[![NPM version](http://img.shields.io/npm/v/react-native-looped-carousel-improved.svg?style=flat)](https://www.npmjs.com/package/react-native-looped-carousel-improved)
[![Dependency Status](https://david-dm.org/felipesousa/react-native-looped-carousel-improved.svg)](https://david-dm.org/felipesousa/react-native-looped-carousel-improved)
[![devDependency Status](https://david-dm.org/felipesousa/react-native-looped-carousel-improved/dev-status.svg)](https://david-dm.org/felipesousa/react-native-looped-carousel-improved#info=devDependencies)

Full-fledged "infinite" (or not) carousel for your [react-native](https://github.com/facebook/react-native/) project. Supports iOS and Android.

Based on [React Native](https://github.com/facebook/react-native/) by Facebook and extends of [react-native-looped-carousel](https://github.com/phil-r/react-native-looped-carousel/) component.

## Demo
![](http://spronin.github.io/img/react.gif)

## Install

```sh
npm install react-native-looped-carousel-improved --save
```

## Documentation Props

Name | propType | default value | description
--- | --- | --- | ---
autoplay | boolean | true | enables auto animations
delay | number | 4000 | number in milliseconds between auto animations
currentPage | number | 0 | allows you to set initial page
pageStyle | style | null | style for pages
contentContainerStyle | style | null | `contentContainerStyle` for the scrollView
onAnimateNextPage | func | null | callback that is called with 0-based Id of the current page
swipe | bool | true | motion control for Swipe
isLooped | bool | true | loop the slide
**Pagination** | --- | --- | ---
pageInfo | boolean | false | shows `{currentPage} / {totalNumberOfPages}` pill at the bottom
pageInfoBackgroundColor | string | 'rgba(0, 0, 0, 0.25)' | background color for pageInfo
pageInfoBottomContainerStyle | style | null | style for the pageInfo container
pageInfoTextStyle | style | null | style for text in pageInfo
pageInfoTextSeparator | string | ' / ' | separator for `{currentPage}` and `{totalNumberOfPages}`
**Bullets** | --- | --- | ---
bullets | bool | false | wether to show "bullets" at the bottom of the carousel
bulletStyle | style | null | style for each bullet
bulletsContainerStyle | style | null | style for the bullets container
chosenBulletStyle | stlye | null | style for the selected bullet
**Arrows** | --- | --- | ---
arrows | bool | false | wether to show navigation arrows for the carousel
arrowsStyle | style | null | style for navigation arrows
arrowsContainerStyle | style | null | style for the navigation arrows container
leftArrowText | string / element | 'Left' | label / icon for left navigation arrow
rightArrowText | string / element | 'Right' | label / icon for right navigation arrow
rightArrowStyle | style | null | style for the right arrow
leftArrowStyle | style | null | style for the left arrow


## Usage
```js
import React, { Component } from 'react';
import {
  Text,
  View,
  Dimensions,
} from 'react-native';
import Carousel from 'react-native-looped-carousel-improved';

const { width, height } = Dimensions.get('window');

export default class MyCarousel extends Component {

  constructor(props) {
    super(props);

    this.state = {
      size: { width, height },
    };
  }

  _onLayoutDidChange = (e) => {
    const layout = e.nativeEvent.layout;
    this.setState({ size: { width: layout.width, height: layout.height } });
  }

  render() {
    return (
      <View style={{ flex: 1 }} onLayout={this._onLayoutDidChange}>
        <Carousel
          delay={2000}
          style={this.state.size}
          autoplay
          pageInfo
          isLooped
          onAnimateNextPage={(p) => console.log(p)}
        >
          <View style={[{ backgroundColor: '#BADA55' }, this.state.size]}><Text>1</Text></View>
          <View style={[{ backgroundColor: 'red' }, this.state.size]}><Text>2</Text></View>
          <View style={[{ backgroundColor: 'blue' }, this.state.size]}><Text>3</Text></View>
        </Carousel>
      </View>
    );
  }
}
```

## Contributing
1. Fork it!

2. Create your feature branch: `git checkout -b my-new-feature`

3. Commit your changes: `git commit -am 'Add some feature'`

4. Push to the branch: `git push origin my-new-feature`

5. Submit a pull request :D

## History

This project is a just improvement to [this project](https://github.com/phil-r/react-native-looped-carousel).

## Credits

All Credits to [@phil-r](https://github.com/phil-r/) to create [react-native-looped-carousel](https://github.com/phil-r/react-native-looped-carousel).

## License

MIT @ Felipe Sousa
