# vue-awesome-dropdown

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
            list: [北京, 上海, 深圳]
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
            list: [北京, 上海, 深圳]
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