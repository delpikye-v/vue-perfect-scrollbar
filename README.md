<div align="center">
    <h1>vue-perfect-scrollbar-z</h1>
    <br />
    <a href="https://codesandbox.io/s/vue-perfect-scrollbar-z-wjl7k">LIVE EXAMPLE</a>
</div>

---

#### Description

+ It is wrap the <b>[perfect-scrollbar](https://github.com/mdbootstrap/perfect-scrollbar)</b> for the element.

+ Auto update scrollbar, you don't have to do anything.

+ Support for scroll-y for only the body of the table. (Hold header)

---

#### Usage
```js
npm install vue-perfect-scrollbar-z --save
```

Import the module in the place you want to use:
```js
/*
if you use perfect-scrollbar in many places you should import css in main file (override avoid)
*/
import 'vue-perfect-scrollbar-z/dist/styles.css';  // > ver 1.0.0

import Scrollbar from 'vue-perfect-scrollbar-z'
```


#### Snippet

##### `simple`

```js
    // tagName = 'div' wrapName='div'
    // something1 = [effect1, effect2, listData, showHide, ..., somthing] // not component
    <Scrollbar height="100px" :effectData="something1" >
        { something1 }
    </Scrollbar>
```

<br />

##### `special tagName (tbody, ul, dl, ol)`

```js
    <Scrollbar
        ref="refScroll"
        tagName="tbody" // tbody, ul, dl, ol
        maxHeight="400px"
        className="list-group"
        :effectData="listData"
        always
        //  @onScrollY="scrolling"  // function scrolling
    >
        ...for data
    </Scrollbar>
```

```js
// access scrollbar (your handler)
let { scrollbar } = this.$refs.refScroll
scrollbar.element.scrollTop = 0 // or something
```
<br />

---

#### props

| props                | type                          | description                                                                |
|----------------------|-------------------------------|----------------------------------------------------------------------------|
| options              | Object                        | [perfect-scrollbar/options](https://github.com/mdbootstrap/perfect-scrollbar#options) |
| tagName              | String                        | Container scrollbar. Default `div`                                         |
| effectData           | String, Array, Object,.....   | Automatically update the scrollbar if the `effectData` has changed.        |
| always               | boolean                       | Always show scrollbar if data is overflow (`true`). Default `false`        |
| maxHeight            | `px, %, vh`                   | max-height of scrollbar                                                    |
| height               | `px, %, vh`                   | height of scrollbar                                                        |
| maxWidth             | `px, %, vw`                   | max-width of scrollbar                                                     |
| width                | `px, %, vw`                   | width of scrollbar                                                         |
| className            | String                        | Your css-class                                                             |
| libTable             | Boolean                       | When you update for 3th-party table. Default `false`                       |
| wrapName             | String                        | Wrap all element scroll (`div`).When tagName is not in [tbody, ul, ol, dl.]|
| wheelStop            | Boolean                       | wheelPropagation (quick in options). Default: `true`. (wheelPropagation or wheelStop) |
| ---                  | ---                           | ---                                                                        |
| @onScrollY           | Function                      | y-axis is scrolled in either direction.                                    |
| @onScrollX           | Function                      | x-axis is scrolled in either direction.                                    |
| @onScrollUp          | Function                      | scrolling upwards.                                                         |
| @onScrollDown        | Function                      | scrolling downwards.                                                       |
| @onScrollLeft        | Function                      | scrolling to the left.                                                     |
| @onScrollRight       | Function                      | scrolling to the right.                                                    |
| @onYReachStart       | Function                      | scrolling reaches the start of the y-axis.                                 |
| @onYReachEnd         | Function                      | scrolling reaches the end of the y-axis (useful for infinite scroll).      |
| @onXReachStart       | Function                      | scrolling reaches the start of the x-axis.                                 |
| @onXReachEnd         | Function                      | scrolling reaches the end of the x-axis (useful for infinite scroll).      |

<br />

#### Note

+ tbody only `scroll-y` (no x).

+ update `scrollTop`, `scrollLeft`: using `document.querySelector(...).scrollTop = 0`... or `refScroll`

+ `ul/ol/dl/tbody`. This is a special (multi childs). So you shouldn't update the border for tagName.

```js
<Scrollbar style={{ border: "1px solid" }} tagName="tbody" ... /> => no

<parent style={{ border: "1px solid" }}> <Scrollbar tagName="tbody" ... /> </parent> => OK
```

+ `libTable`
```js
<Scrollbar libTable={true}><CustomTag></CustomTag></Scrollbar>

It will try to add the perfect scrollbar to the `tbody` of the `first` table found. (Checking...)

```

+ you should use `ul/dl/ol` with basic
```js
    <Scrollbar :effectData="abcd" .... > <ul> <for>...</for> </ul> <Scrollbar>
```

+ Some cases when you scroll to bottom and remove item data. It leaves empty space. (Some other libs)
=>  It has check here.

<br />

#### RUN

<a href="https://codesandbox.io/s/vue-perfect-scrollbar-z-8ikb5">LIVE EXAMPLE</a>

```js
npm install
```
```js
npm run dev
npm run start
```

### License

MIT
