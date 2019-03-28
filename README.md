# vue-awesome-dropdown

<a href="https://badge.fury.io/js/vue-awesome-dropdown"><img src="https://badge.fury.io/js/vue-awesome-dropdown.svg" alt="npm version" height="18"></a>

> A dropdown refresh component implements by vuejs 2.0 for mobile.

## Usage

### Install

```bash
npm install vue-awesome-dorpdown --save
```

### CommonJS

```javascript
var DropDown = require('vue-awesome-dropdown');

new Vue({
    components: { DropDown },
    data: function () {
        return {
            name: "",
            list: [
                { name: "北京" },
                { name: "上海" },
                { name: "深圳" },
            ]
        };
    },
    template: '<drop-down v-model="name" :list="list" :></drop-down>'
});
```

### ES6
```javascript
import DropDown from 'vue-awesome-dropdown';

new Vue({
    components: { DropDown },
    data: function () {
        return {
            name: "",
            list: [
                { name: "北京" },
                { name: "上海" },
                { name: "深圳" },
            ]
        };
    },
    template: '<drop-down v-model="name" :list="list" :></drop-down>'
});
```

### Props
| Property | Description |
|:--|:--|
| name | 默认选中的项 |
| list | 可选列表 |

## License

[MIT](http://opensource.org/licenses/MIT)