# 1 项目创建

### 1.电脑上安装node.js

网址：https://nodejs.org/zh-cn/

下载自己对应操作系统版本 安装即可

### 2.全局下载项目脚手架

打开cmd 输入 npm install -g @vue/cli

### 3.创建项目

把cmd的路径切换到指定路径下  vue create 项目名  

(3-1)选择项目配置模板  **选择第三项**自主选择你项目所需的配置

```
Please pick a preset: 
  Default ([Vue 2] babel, eslint) vue cli 2 默认的项目模板
  Default (Vue 3 Preview) ([Vue 3] babel, eslint) vue cli 3 默认的项目模板
❯ Manually select features 
```



(3-2)选择项目配置选项   勾选所需要的模块

```
? Check the features needed for your project: 
 ◉ Babel
 ◉ TypeScript
 ◯ Progressive Web App (PWA) Support
 ◉ Router
 ◉ Vuex
❯◉ CSS Pre-processors
 ◉ Linter / Formatter
 ◯ Unit Testing
 ◯ E2E Testing


```

(3-3)选择想要开始项目的Vue.js版本  选择 3.x

```
? Choose a version of Vue.js that you want to start the project with (Use arrow keys)
❯ 3.x 
  2.x  


```

(3-4)是否使用Class风格装饰器？选择默认N

```
Use class-style component syntax? (y/N)
```

(3-5)使用babel来编译ts 选择默认Y

```
Use Babel alongside TypeScript (required for modern mode, auto-detected polyfills, 
transpiling JSX)? (Y/n)
```



(3-6)是否用history模式来创建路由  直接回车默认项目

```
? Use history mode for router? (Requires proper server setup for index fallback in pr
oduction) (Y/n) 
```

(3-7)选择CSS 预处理类型  选择第一项

```
 Pick a CSS pre-processor (PostCSS, Autoprefixer and CSS Modules are supported by 
default): (Use arrow keys)
❯ Sass/SCSS (with dart-sass) 
  Less 
  Stylus 
```

(3-8) 选择代码校验会犯 选择第一项  只进行报错提醒

```
? Pick a linter / formatter config: (Use arrow keys)
❯ ESLint with error prevention only 
  ESLint + Airbnb config 
  ESLint + Standard config 
  ESLint + Prettier 
```

(3-9)询问项目的什么时候校验格式(第一个是保存时，第二个是提交时)

```
? Pick additional lint features: (Press <space> to select, <a> to toggle all, <i> to 
invert selection)
❯◉ Lint on save
 ◯ Lint and fix on commit
```

(3-10)询问项目的配置文件放在那里 (1.独立文件   2.package.json中)

```
? Where do you prefer placing config for Babel, ESLint, etc.? (Use arrow keys)
❯ In dedicated config files 
  In package.json 
```

(3-11)是否保存配置当做后续项目的可选配置  我们选择不保存

```
? Save this as a preset for future projects? (y/N) 
```

### 4运行项目

把cmd的路径切换到你项目名下

npm run serve 启动项目





# 2初始化项目

1在第一次创建好项目之后发现app.vue中的router-view有个如下错误 爆红

```
[vue/no-multiple-template-root]
The template root requires exactly one element.
```

删除app.vue下的默认样式与 路由导航（这是因为vue的模版中只能有一个根节点，所以在<template>中插入第二个元素就会报错）

2.删除components下的hellowoed文件

3.删除views下的文件

4.在views下新建login文件夹其中新建index.vue（登录页）



````vue
<template>
  <div class="login">
      登录页
  </div>
</template>

<script>
export default {

}
</script>

<style lang="scss">
  .login {
    background-color:#000066;//深蓝色
    height: 100%;
  }
  html,body,#app{//设置页面100%高
       height: 100%;
  }
</style>
````



**注意：在最新脚手架项目中 .vue文件的命名方式默认是大驼峰命名法(首字母大写其后每个单词的首字母也是大写)** 

注意：也可以关闭eslint验证不使用驼峰 在vue.config.js中配置

```js
const { defineConfig } = require('@vue/cli-service')
module.exports = defineConfig({
  transpileDependencies: false,
  lintOnSave: true,//设置是否在开发环境下每次保存代码时都启用 eslint验证
  // false：关闭每次保存都进行检测
  // true：开启每次保存都进行检测，效果与warning一样
  // ‘warning’：开启每次保存都进行检测，lint 错误将显示到控制台命令行，而且编译并不会失败。
  // ‘error’：开启每次保存都进行检测，lint 错误将显示到浏览器页面上，且编译失败。
  // ‘default’：同’error’
})

```



5.配置路由router下的index.js





# 3修改默认样式

1.配置css主文件入口 方便后期进行样式的设置

在根路径下新建vue.config.js 来进行webpack的配置(3.0项目中自带)

```js
const { defineConfig } = require('@vue/cli-service')
module.exports = defineConfig({
  transpileDependencies: true,
  },
})


```

2.设置css住入口文件配置在vue.config.js中设置

```js
 // css相关配置
  css: {
    // css预设器配置项
    loaderOptions: {
      scss: { 
        additionalData: `@import "./src/styles/style.scss";`//主入口css文件路径
      }
    }
  }
```

3.新建styles 文件夹 并新建 main.scss 主样式文件 并且写入初始化样式

```css
html,
body,
div,
span,
applet,
object,
iframe,
h1,
h2,
h3,
h4,
h5,
h6,
p,
blockquote,
pre,
a,
abbr,
acronym,
address,
big,
cite,
code,
del,
dfn,
em,
img,
ins,
kbd,
q,
s,
samp,
small,
strike,
strong,
sub,
sup,
tt,
var,
b,
u,
i,
center,
dl,
dt,
dd,
ol,
ul,
fieldset,
form,
label,
legend,
table,
caption,
tbody,
tfoot,
thead,
tr,
th,
td,
article,
aside,
canvas,
details,
embed,
figure,
figcaption,
footer,
header,
hgroup,
menu,
nav,
output,
ruby,
section,
summary,
time,
mark,
audio,
video {
  margin: 0;
  padding: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
}

article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
menu,
nav,
section {
  display: block;
}

html {
  line-height: 1.15;
  -webkit-text-size-adjust: 100%;
}

body {
  margin: 0;
  background-color: #f7f7f7;
  font-family: 'Microsoft YaHei';
  font-size: 15px;
}

main {
  display: block;
}

a {
  background-color: transparent;
  text-decoration: none;
}

img {
  display: block;
  border-style: none;
}

ul,
li {
  list-style: none;
}
```

4.引入到主样式文件中 在style.scss文件中编写

```css
@import "./main.scss"
```

# 4 Element Plus项目集成

官网：https://element-plus.gitee.io/zh-CN/#/zh-CN/component/installation

1.安装

```
npm install element-plus --save
```

2.完整引入（不推荐 但是引用简单）

```js
import { createApp } from 'vue'
import App from './App.vue'
import router from './router'
import store from './store'
// 1.引用
import ElementPlus from 'element-plus'
import 'element-plus/dist/index.css'

// 2.use使用elementplus
createApp(App).use(store).use(router).use(ElementPlus).mount('#app')

```

3.按需导入--自动导入

1.首先你需要安装`unplugin-vue-components` 和 `unplugin-auto-import`这两款插件

```
npm install -D unplugin-vue-components unplugin-auto-import
```

2.在vue.config.js中配置

```js
const { defineConfig } = require('@vue/cli-service')

const AutoImport = require('unplugin-auto-import/webpack')
const Components = require('unplugin-vue-components/webpack')
const { ElementPlusResolver } = require('unplugin-vue-components/resolvers')
module.exports = defineConfig({
  transpileDependencies: true,
  // 设置插件配置
  configureWebpack: {
    plugins: [
      AutoImport({
        resolvers: [ElementPlusResolver()],
      }),
      Components({
        resolvers: [ElementPlusResolver()],
      }),
    ]
  }
})

```

3.就可以直接使用了(在使用之前不要忘了重新启动项目)

# 5登录注册tab切换

1.创建切换数据在login下的index.vue

```vue
<script lang="ts" setup>
import { reactive, ref } from "vue";
/**
 * 创建变量
 */
const menuData = reactive([
  { txt: "登录", current: true, type: "login" },
  { txt: "注册", current: false, type: "register" },
]);
const model = ref("login");

</script>

```

2.在页面循环数据并且设置点击调用函数 进行切换

```vue
<template>
  <div class="login">
    <div class="login-con">
      <!-- 顶部切换 -->
      <ul class="menu-tab">
        <li
          v-for="item in menuData"
          :key="item.id"
          :class="{ current: item.current }"
          @click="clickMenu(item)"
        >
          {{ item.txt }}
        </li>
      </ul>
    </div>
  </div>
</template>
```

3.创建对应函数

```js
/**
 * 声明函数
 */
// 切换模块
const clickMenu = (data) => {
  //先让所有的数据都变成false没有选中状态
  menuData.forEach((elem) => {
    elem.current = false;
  });
  // 在让点击的哪一项编程选中状态
  data.current = true;
  // 修改模块值
  model.value = data.type;
};
```

4设置样式

```vue
<style lang="scss">
.login {
  background-color: #000066; //深蓝色
  height: 100%;
}
html,
body,
#app {
  //设置页面100%高
  height: 100%;
}

// 设置切换样式开始
.login-wrap {
  width: 330px;
  margin: auto;
}
.menu-tab {
  text-align: center;
  li {
    display: inline-block;
    width: 88px;
    line-height: 36px;
    font-size: 14px;
    color: #fff;
    border-radius: 2px;
    cursor: pointer;
  }
  .current {
    background-color: rgba(255, 255, 255, 0.5);//白色半透明
  }
}
// 设置切换样式结束
</style>
```

完整代码

```vue

<template>
  <div class="login">
    <div class="login-con">
      <!-- 顶部切换 -->
      <ul class="menu-tab">
        <li
          v-for="item in menuData"
          :key="item.id"
          :class="{ current: item.current }"
          @click="clickMenu(item)"
        >
          {{ item.txt }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { reactive, ref } from "vue";
/**
 * 创建变量
 */
const menuData = reactive([
  { txt: "登录", current: true, type: "login" },
  { txt: "注册", current: false, type: "register" },
]);
const model = ref("login");

/**
 * 声明函数
 */
// 切换模块
const clickMenu = (data) => {
  menuData.forEach((elem) => {
    elem.current = false;
  });
  // 高光
  data.current = true;
  // 修改模块值
  model.value = data.type;
};
</script>

<style lang="scss">
.login {
  background-color: #000066; //深蓝色
  height: 100%;
}
html,
body,
#app {
  //设置页面100%高
  height: 100%;
}

// 设置切换样式开始
.login-wrap {
  width: 330px;
  margin: auto;
}
.menu-tab {
  text-align: center;
  li {
    display: inline-block;
    width: 88px;
    line-height: 36px;
    font-size: 14px;
    color: #fff;
    border-radius: 2px;
    cursor: pointer;
  }
  .current {
    background-color: rgba(255, 255, 255, 0.5);//白色半透明
  }
}
// 设置切换样式结束
</style>
```

# 6elementPlus表单基本使用

1.把elementplus中表单--》自定义校验规则中的内容放置到 登录页面中

(1)html部分

````vue

<template>
  <div class="login">
    <div class="login-con">
      <!-- 顶部切换 -->
      <ul class="menu-tab">
        <li
          v-for="item in menuData"
          :key="item.id"
          :class="{ current: item.current }"
          @click="clickMenu(item)"
        >
          {{ item.txt }}
        </li>
      </ul>

      <!-- 表单部分 -->
      <el-form
        ref="ruleFormRef"
        :model="ruleForm"
        status-icon
        :rules="rules"
        label-width="120px"
        class="demo-ruleForm"
      >
        <el-form-item label="Password" prop="pass">
          <el-input
            v-model="ruleForm.pass"
            type="password"
            autocomplete="off"
          />
        </el-form-item>
        <el-form-item label="Confirm" prop="checkPass">
          <el-input
            v-model="ruleForm.checkPass"
            type="password"
            autocomplete="off"
          />
        </el-form-item>
        <el-form-item label="Age" prop="age">
          <el-input v-model.number="ruleForm.age" />
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="submitForm(ruleFormRef)"
            >Submit</el-button
          >
          <el-button @click="resetForm(ruleFormRef)">Reset</el-button>
        </el-form-item>
      </el-form>
        <!-- 表单部分 -->
    </div>
  </div>
</template>
````

（2）js部分

```js

import type { FormInstance } from "element-plus";

const ruleFormRef = ref<FormInstance>();

const checkAge = (rule: any, value: any, callback: any) => {
  if (!value) {
    return callback(new Error("Please input the age"));
  }
  setTimeout(() => {
    if (!Number.isInteger(value)) {
      callback(new Error("Please input digits"));
    } else {
      if (value < 18) {
        callback(new Error("Age must be greater than 18"));
      } else {
        callback();
      }
    }
  }, 1000);
};

const validatePass = (rule: any, value: any, callback: any) => {
  if (value === "") {
    callback(new Error("Please input the password"));
  } else {
    if (ruleForm.checkPass !== "") {
      if (!ruleFormRef.value) return;
      ruleFormRef.value.validateField("checkPass", () => null);
    }
    callback();
  }
};
const validatePass2 = (rule: any, value: any, callback: any) => {
  if (value === "") {
    callback(new Error("Please input the password again"));
  } else if (value !== ruleForm.pass) {
    callback(new Error("Two inputs don't match!"));
  } else {
    callback();
  }
};

const ruleForm = reactive({
  pass: "",
  checkPass: "",
  age: "",
});

const rules = reactive({
  pass: [{ validator: validatePass, trigger: "blur" }],
  checkPass: [{ validator: validatePass2, trigger: "blur" }],
  age: [{ validator: checkAge, trigger: "blur" }],
});

const submitForm = (formEl: FormInstance | undefined) => {
  if (!formEl) return;
  formEl.validate((valid) => {
    if (valid) {
      console.log("submit!");
    } else {
      console.log("error submit!");
      return false;
    }
  });
};

const resetForm = (formEl: FormInstance | undefined) => {
  if (!formEl) return;
  formEl.resetFields();
};

```

2.设置页面布局  把原本在输入框左边的文字设置到上面 并且设置相关输入框内容

```vue
<template>
  <div class="login">
    <div class="login-con">
      <!-- 顶部切换 -->
      <ul class="menu-tab">
        <li
          v-for="item in menuData"
          :key="item.id"
          :class="{ current: item.current }"
          @click="clickMenu(item)"
        >
          {{ item.txt }}
        </li>
      </ul>

      <!-- 表单部分 -->
      <el-form
        ref="ruleFormRef"
        :model="ruleForm"
        status-icon
        :rules="rules"
        label-width="120px"
        class="demo-ruleForm"
      >
        <!-- 修改提示文字 并且修改type类型 与v-model绑定的数据 并且添加类名-->
        <el-form-item prop="pass" class="item-from">
          <label for="username">邮箱</label>
          <el-input
            v-model="ruleForm.username"
            type="text"
            autocomplete="off"
          />
        </el-form-item>
        <el-form-item prop="password" class="item-from">
          <label for="password">密码</label>
          <el-input
            id="password"
            type="password"
            v-model="ruleForm.password"
            autocomplete="off"
            minlength="6"
            maxlength="20"
          ></el-input>
        </el-form-item>

        <el-form-item
          prop="passwords"
          class="item-from"
        >
          <label>重复密码</label>
          <el-input
            type="password"
            v-model="ruleForm.passwords"
            autocomplete="off"
            minlength="6"
            maxlength="20"
          ></el-input>
        </el-form-item>
        <!-- 设置按钮 -->
        <el-form-item>
          <el-button type="danger"  class="login-btn block" >登录</el-button>
        </el-form-item>
      </el-form>
      <!-- 表单部分 -->
    </div>
  </div>
</template>
```

3.设置样式

3-1删除el-form标签上面的默认label-width属性

3-2设置相关样式

````css
// 表单样式
.demo-ruleForm {
  width: 30%;
margin: 50px auto;
  label {
    display: block;
    margin-bottom: 3px;
    font-size: 14px;
    color: #fff;
  }
  .item-from { 
    margin-bottom: 13px; 
    }
  .block {
    display: block;
    width: 100%;
  }
  .login-btn { margin-top: 19px; }
  
}

// 表单样式
````

完整代码

```vue

<template>
  <div class="login">
    <div class="login-con">
      <!-- 顶部切换 -->
      <ul class="menu-tab">
        <li
          v-for="item in menuData"
          :key="item.id"
          :class="{ current: item.current }"
          @click="clickMenu(item)"
        >
          {{ item.txt }}
        </li>
      </ul>

      <!-- 表单部分 -->
      <el-form
        ref="ruleFormRef"
        :model="ruleForm"
        status-icon
        :rules="rules"
       
        class="demo-ruleForm"

      >
        <!-- 修改提示文字 并且修改type类型 与v-model绑定的数据 并且添加类名-->
        <el-form-item prop="pass" class="item-from">
          <label for="username">邮箱</label>
          <el-input
            v-model="ruleForm.username"
            type="text"
            autocomplete="off"
          />
        </el-form-item>
        <el-form-item prop="password" class="item-from">
          <label for="password">密码</label>
          <el-input
            id="password"
            type="password"
            v-model="ruleForm.password"
            autocomplete="off"
            minlength="6"
            maxlength="20"
          ></el-input>
        </el-form-item>

        <el-form-item
          prop="passwords"
          class="item-from"
        >
          <label>重复密码</label>
          <el-input
            type="password"
            v-model="ruleForm.passwords"
            autocomplete="off"
            minlength="6"
            maxlength="20"
          ></el-input>
        </el-form-item>
        <!-- 设置按钮 -->
        <el-form-item>
          <el-button type="danger"  class="login-btn block" >登录</el-button>
        </el-form-item>
      </el-form>
      <!-- 表单部分 -->
    </div>
  </div>
</template>

<script lang="ts" setup>
import { reactive, ref } from "vue";
/**
 * 顶部切换变量
 */
const menuData = reactive([
  { txt: "登录", current: true, type: "login" },
  { txt: "注册", current: false, type: "register" },
]);
const model = ref("login");

/**
 * 顶部切换声明函数
 */
// 切换模块
const clickMenu = (data) => {
  menuData.forEach((elem) => {
    elem.current = false;
  });
  // 高光
  data.current = true;
  // 修改模块值
  model.value = data.type;
};

// 表单验证
import type { FormInstance } from "element-plus";

const ruleFormRef = ref<FormInstance>();

const checkAge = (rule: any, value: any, callback: any) => {
  if (!value) {
    return callback(new Error("Please input the age"));
  }
  setTimeout(() => {
    if (!Number.isInteger(value)) {
      callback(new Error("Please input digits"));
    } else {
      if (value < 18) {
        callback(new Error("Age must be greater than 18"));
      } else {
        callback();
      }
    }
  }, 1000);
};

const validatePass = (rule: any, value: any, callback: any) => {
  if (value === "") {
    callback(new Error("Please input the password"));
  } else {
    if (ruleForm.checkPass !== "") {
      if (!ruleFormRef.value) return;
      ruleFormRef.value.validateField("checkPass", () => null);
    }
    callback();
  }
};
const validatePass2 = (rule: any, value: any, callback: any) => {
  if (value === "") {
    callback(new Error("Please input the password again"));
  } else if (value !== ruleForm.pass) {
    callback(new Error("Two inputs don't match!"));
  } else {
    callback();
  }
};

const ruleForm = reactive({
  pass: "",
  checkPass: "",
  age: "",
});

const rules = reactive({
  pass: [{ validator: validatePass, trigger: "blur" }],
  checkPass: [{ validator: validatePass2, trigger: "blur" }],
  age: [{ validator: checkAge, trigger: "blur" }],
});

const submitForm = (formEl: FormInstance | undefined) => {
  if (!formEl) return;
  formEl.validate((valid) => {
    if (valid) {
      console.log("submit!");
    } else {
      console.log("error submit!");
      return false;
    }
  });
};

const resetForm = (formEl: FormInstance | undefined) => {
  if (!formEl) return;
  formEl.resetFields();
};

// 表单验证结束
</script>

<style lang="scss">
.login {
  background-color: #000066; //深蓝色
  height: 100%;
}
html,
body,
#app {
  //设置页面100%高
  height: 100%;
}

// 设置切换样式开始
.login-wrap {
  width: 330px;
  margin: auto;
}
.menu-tab {
  text-align: center;
  li {
    display: inline-block;
    width: 88px;
    line-height: 36px;
    font-size: 14px;
    color: #fff;
    border-radius: 2px;
    cursor: pointer;
  }
  .current {
    background-color: rgba(255, 255, 255, 0.5); //白色半透明
  }
}
// 设置切换样式结束

// 表单样式
.demo-ruleForm {
  width: 30%;
margin: 50px auto;
  label {
    display: block;
    margin-bottom: 3px;
    font-size: 14px;
    color: #fff;
  }
  .item-from { 
    margin-bottom: 13px; 
    }
  .block {
    display: block;
    width: 100%;
  }
  .login-btn { margin-top: 19px; }
  
}

// 表单样式
</style>
```

# 7登录注册tab切换功能实现

在每次切换登录注册的时候页面的展示内容是不相同的所以我们需要进行对应内容的设置

1.在注册的时候 重复密码是不显示的 所以我们进行v-show的设置

```html
    <!-- 给重复密码设置v-show控制显示和隐藏 -->
        <el-form-item
          prop="passwords"
          class="item-from"
          v-show="model === 'register'"
        >
          <label>重复密码</label>
          <el-input
            type="password"
            v-model="ruleForm.passwords"
            autocomplete="off"
            minlength="6"
            maxlength="20"
          ></el-input>
        </el-form-item>
```

2.给按钮设置切换 显示登录或者注册

```html
 <!-- 设置按钮 -->
        <el-form-item>
          <el-button type="danger"  class="login-btn block" >{{ model === 'login' ? "登录" : "注册" }}</el-button>
        </el-form-item>
```

# 8elementplus表单验证设置

1.修改elementplus提供的输入框绑定变量

```js
// 输入框中绑定的变量
const ruleForm = reactive({
  username: "",
  password: "",
  passwords: "",
});
```

2.修改触发验证的变量设置

````js
// 这里是设置设置 以何种方式触发 表单验证 默认是blur失去焦点验证
// 当触发了blur事件后就会调用前面的 函数从而进行表单验证
const rules = reactive({
  password: [{ validator: validatePass, trigger: "blur" }],
  passwords: [{ validator: validatePass2, trigger: "blur" }],
  username: [{ validator: checkUser, trigger: "blur" }],//修改名字 并且修改上面的函数名
});
````

3.设置邮箱验证

(3-1)修改邮箱输入框的prop属性为username

```html
 <el-form-item prop="username" class="item-from">
```

(3-2)修改对应触发函数

```js
const checkUser = (rule: any, value: any, callback: any) => {
  // 创建邮箱正则来进行邮箱格式校验
  let reg = /^([a-zA-Z]|[0-9])(\w|\-)+@[a-zA-Z0-9]+\.([a-zA-Z]{2,4})$/; 
  if (!value) {
    return callback(new Error("邮箱不能为空！！"));
  } else if(!reg.test(value)){
    return callback(new Error("邮箱格式有误！！"));
  }else{
     callback();
  }
};
```

4.设置密码验证

（4-1）修改密码输入框的prop属性为password

```html
   <el-form-item prop="password" class="item-from">
```

(4-2)修改对应触发函数

```js
const validatePass = (rule: any, value: any, callback: any) => {
  let reg = /^(?!\D+$)(?![^a-zA-Z]+$)\S{6,15}$/;// 验证密码 6至15位的字母+数字 
  if (value === "") {
    callback(new Error("密码不能为空"));
  }else if(!reg.test(value)){
  callback(new Error("密码格式有误!6至15位的字母+数字"));
  } else {
    callback();
  }
};
```

5.设置重复密码验证

（5-1）修改重复密码输入框的prop属性为passwords

```html
 <el-form-item prop="passwords" class="item-from" v-show="model === 'register'">
```

(5-2)修改对应触发函数

````js
const validatePass2 = (rule: any, value: any, callback: any) => {

  if (value === "") {
    callback(new Error("重复密码不能为空"));
  } else if (value !== ruleForm.password) {
    callback(new Error("两次密码必须相同"));
  } else {
    callback();
  }
};
````

6.设置提交按钮

1.给按钮绑定事件(在初始化的时候elementplus官网已经写好了)

```
  <el-button @click="submitForm(ruleFormRef)" type="danger" class="login-btn block">{{
            model === "login" ? "登录" : "注册"
          }}</el-button>
```

2.调用函数

````js
const submitForm = (formEl: FormInstance | undefined) => {
  if (!formEl) return;
  formEl.validate((valid) => {
    if (valid) {
      console.log("submit!");
    } else {
      console.log("error submit!");
      return false;
    }
  });
};
````

7 因为登录没有重复密码 所以在登录的时候跳过 所以在重复密码哪里添加判断

````js
const validatePass2 = (rule: any, value: any, callback: any) => {
 // 因为登录没有重复密码 所以在登录的时候跳过
  if(model.value === 'login') { callback(); }
  
  
  if (value === "") {
    callback(new Error("重复密码不能为空"));
  } else if (value !== ruleForm.password) {
    callback(new Error("两次密码必须相同"));
  } else {
    callback();
  }
};
````

# 9封装工具库

上一节课大家会发现页面中 对于邮箱的验证和密码的验证可能在很多地方都会使用到  每次如果要使用 在重复编写一次很麻烦 所以我们可以把这个验证的内容 封装成一个工具 在想使用的地方进行使用

1.新建util文件夹用来容纳工具文件

2.新建.js文件用来容纳代码(verification.js)

3.写入如下验证

```js
/**
 * 验证邮箱
 */
 export function verificationEmail(data){
    let reg = /^([a-zA-Z]|[0-9])(\w|\-)+@[a-zA-Z0-9]+\.([a-zA-Z]{2,4})$/; 
    return reg.test(data)===false ? true : false;
}
/**
 * 验证密码 6至15位的字母+数字 
 */
export function verificationPwd(data){
    let reg = /^(?!\D+$)(?![^a-zA-Z]+$)\S{6,15}$/;
    return !reg.test(data) ? true : false;
}
```

4.在想使用的地方 引用使用（在login下的index中）

````js
// 引用验证工具库
import * as verification from "../../util/verification.js"

在表单验证地方调用
const checkUser = (rule: any, value: any, callback: any) => {
  // 创建邮箱正则来进行邮箱格式校验
  // let reg = /^([a-zA-Z]|[0-9])(\w|\-)+@[a-zA-Z0-9]+\.([a-zA-Z]{2,4})$/; 
  if (!value) {
    return callback(new Error("邮箱不能为空！！"));
    // 调用验证（注意删掉之前的取反）
  } else if(verification.verificationEmail(value)){
    return callback(new Error("邮箱格式有误！！"));
  }else{
     callback();
  }
};

const validatePass = (rule: any, value: any, callback: any) => {
  // let reg = /^(?!\D+$)(?![^a-zA-Z]+$)\S{6,15}$/;// 验证密码 6至15位的字母+数字 
  if (value === "") {
    callback(new Error("密码不能为空"));
    // 调用验证
  }else if(verification.verificationPwd(value)){
  callback(new Error("密码格式有误!6至15位的字母+数字"));
  } else {
    callback();
  }
};
````



# 10axios封装与拦截器

## 拦截器

**请求拦截器**
请求拦截器的作用是在请求发送前进行一些操作，例如在每个请求体里加上token，统一做了处理如果以后要改也非常容易。

**响应拦截器**
响应拦截器的作用是在接收到响应后进行一些操作，例如在服务器返回登录状态失效，需要重新登录的时候，跳转到登录页。

1.下载axios  npm install --save axios

2.在util下新建service文件用来容纳拦截器

```js
import axios from "axios"
// 创建axios 赋值给常量service 
const service = axios.create();

// 添加请求拦截器（Interceptors）
service.interceptors.request.use(function (config) {
    // 发送请求之前做写什么
    return config;
  }, function (error) {
    // 请求错误的时候做些什么
    return Promise.reject(error);
  });

// 添加响应拦截器
service.interceptors.response.use(function (response) {
    // 对响应数据做点什么
    return response;
  }, function (error) {
    // 对响应错误做点什么
    return Promise.reject(error);
  });
  export default service

```

## axios封装

3.创建api文件夹  并且创建对应.js文件用来容纳请求

```js
import service from "../../util/service.js"

let link=(url,method="GET",data={},params={})=>{
    return new Promise((resolve,reject)=>{
        service.request({
            url,
            method,
            data,
            params
        }).then((ok)=>{
            resolve(ok)
        }).catch((err)=>{
            reject(err)
        })
    })
}

export default link
```

4.在想使用的地方引用调用使用

# 11json-server

在项目中用来进行模拟数据的    

1.下载   npm install -g json-server

2.查看版本  json-server --version

3.创建模拟数据文件夹mock 在其中写入数据的json文件

```
 {
    "one":[
        {"name":"xixi","age":18}
    ]
}
```

4.启动

（4-1）cd到mock文件夹下

（4-2）json-server --watch 你的json文件名字 --port 你的端口

疑问  上面这个名字太难记了  我怎么修改他？

1.cd到mock文件夹下   npm init -y   初始化一个package.json 文件

2。到package.json文件中  在scripts节点中设置你的启动命令

```js
{
  "name": "mock",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
      我是配置启动命令的
    "xiaoming":"json-server --watch data.json --port 8877", 
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}

```

3. 启动  npm run 你的配置名字即可



## 请求

在要使用请求的地方

```
引用api封装的请求
import link from "../../api/link.js"

使用请求
const submitForm = (formEl: FormInstance | undefined) => {
  if (!formEl) return;
  formEl.validate((valid) => {
    if (valid) {
      console.log("submit!");

      // 发送请求
      link("http://localhost:8888/one").then((ok)=>{
        console.log(ok)
      })

    } else {
      console.log("error submit!");
      return false;
    }
  });
};
```

# 12 vue环境部署与baseurl配置

## 环境变量

在开发的时候一般会有是三个环境：开发环境 测试环境 线上环境

**vue 中有个概念就是模式，默认先vue cli 有三个模式**

- `development`开发环境模式用于 vue-cli-service serve
- `production`生产环境模式用于 vue-cli-service build 和 vue-cli-service test:e2e
- `test`测试环境模式用于 vue-cli-service test:unit



**但是往往开发的时候可能不止有三种：**

- 本地环境（local）
- 开发环境（development）
- 测试环境（devtest）
- 预发布环境（beta）
- 生产环境（production）



### 创建不同环境变量文件

通过为.env文件增加后缀来设置某个模式下特有的环境变量。

1.在项目根路径下设置  新建对应文件 .env.development（开发环境文件） .env.production（生产环境文件）.env.devtest（测试环境文件）

2.在每个文件写入如下内容(VUE_APP_随便写）

```
VUE_APP_XIAOMING = "开发模式"
```

### package.json环境对应的执行语句

```
  "scripts": {
    "serve": "vue-cli-service serve",//开发模式
    "build": "vue-cli-service build",//生产模式
    "dev_test_build": "vue-cli-service build --mode development_test",//测试模式
    "lint": "vue-cli-service lint"

  },
```



使用变量process.env.你的内容即可得到

```
import { reactive, ref,onMounted} from "vue";

onMounted(()=>{

    console.log(process.env.VUE_APP_XIAOMING);

   

})
```

## 默认请求地址baseurl

因为我们可以配置不同的环境变量 那么我们就可以在设置请求的时候  根据不同的环境来设置不同的请求地址

1.在开发环境文件中配置我们的请求（今后开发的时候可以在其他配置文件中配置你的请求）

```
VUE_APP_XIAOMING = "开发模式"
VUE_APP_API = "http://localhost:8888"
```



2.在封装的拦截器文件中配置baseURL

```js
let axiosurl = ""
// 如果为开发模式的话执行url
if(process.env.NODE_ENV === 'development' ){
  axiosurl=process.env.VUE_APP_API
}else{
  // 否则设置成其他的模式（这里今后有很多个判断）
  axiosurl=process.env.VUE_APP_API
}

// 创建axios 赋值给常量service 
const service = axios.create({
  baseURL: axiosurl
});

```

3.在今后的请求中直接写请求的路由地址就行

```js
    // 发送请求 url中请求地址前缀已经在baseURL中配置了
      link("/one").then((ok)=>{
        console.log(ok)
      })
```

# 13注册功能实现

## 数据设置

1.在json-server中设置一个注册接口在index.json中新建register节点

```json
{
    "one":[
        {"name":"xixi","age":18}
    ],
    "register":[
        {"id":1, "name":"admin","pwd":"admin"}
    ]
}
```

2.判断是登录还是注册

## 数据发送

3.把输入框的数据发送给后台

````js
const submitForm = (formEl: FormInstance | undefined) => {
  if (!formEl) return;
  formEl.validate((valid) => {
    if (valid) {
      // 判断是登录还是注册
      if (model.value == "login") {
        console.log("登录");
      } else {
        // 把要发送的数据拼装成一个对象
        let data = {
          uname: ruleForm.username,
          pwd: ruleForm.password,
        };

        link("/register", "POST", data).then((ok) => {
          console.log(ok);
        });
      }
    } else {
      console.log("error submit!");
      return false;
    }
  });
};
````



4.判断注册是否成功

```js
  link("/register", "POST", data).then((ok) => {
          
          // 判断数据是否为空 不为空表示注册成功
          let {data}=ok
          // 转成成数组判断长度即可知道对象是否为空
          if(Object.keys(data).length!==0){
            console.log("注册成功！")
          }else{
            console.log("注册失败")
          }
        });
```

## elementplus--Message

5.设置提示框

在main.ts中

```js
import { createApp } from 'vue'
import App from './App.vue'
import router from './router'
import store from './store'
// 引用
import ElementPlus from 'element-plus'
import 'element-plus/dist/index.css'

// 使用
createApp(App).use(store).use(router).use(ElementPlus).mount('#app')

```



在登录页面使用

```js
  link("/register", "POST", data).then((ok) => {
          ElMessage.error("注册失败");
          // 判断数据是否为空 不为空表示注册成功
          let { data } = ok;
          // 转成成数组判断长度即可知道对象是否为空
          if (Object.keys(data).length !== 0) {
            ElMessage("注册成功");
          } else {
            ElMessage.error("注册失败");
          }
        });
```

## 注册成功后切换到 登录页面

在注册成功的地方设置 控制切换的变量为login

```js
    link("/register", "POST", data).then((ok) => {
          ElMessage.error("注册失败");
          // 判断数据是否为空 不为空表示注册成功
          let { data } = ok;
          // 转成成数组判断长度即可知道对象是否为空
          if (Object.keys(data).length !== 0) {
            ElMessage("注册成功");
            
            
          //  把输入框的内容切换到登录
            model.value="login"

           
          } else {
            ElMessage.error("注册失败");
          }
        });
```



设置顶部切换为登录页面

```js
  link("/register", "POST", data).then((ok) => {
          ElMessage.error("注册失败");
          // 判断数据是否为空 不为空表示注册成功
          let { data } = ok;
          // 转成成数组判断长度即可知道对象是否为空
          if (Object.keys(data).length !== 0) {
            ElMessage("注册成功");
          //  把输入框的内容切换到登录
            model.value="login"
            
            
            // 把上面的切换按钮编程登录
            // 先把所有的的控制切换的变量编程false
              menuData.forEach((elem) => {
                elem.current = false;
              });
              // 在吧登录的编程true
              menuData[0].current=true;

           
          } else {
            ElMessage.error("注册失败");
          }
        });
```

# 14 响应拦截器

响应拦截器的作用是在接收到响应后进行一些操作

响应拦截器也是一样如此，就是在请求结果返回后，先不直接显示错误，而是先对响应码等等进行处理，处理好后再导出给页面一个错误提醒

1.在util文件夹下的service.js中打印相应信息（需要关闭后台或者修改下错误路径）会发现得到了不同的错误信息

```js

service.interceptors.response.use(function (response) {
    return response;
  }, function (error) {
      //  打印下看看当错误的时候干什么
  console.log("aaaaaa",error);
 
    return Promise.reject(error);
  });
  export default service
```

2.得到失败响应的status(状态码)需要在response中获得  error.response.status

```js
  console.log("aaaaaa", error.response.status);
```

3 可以对错误信息进行设置

```js
      //  打印下看看当错误的时候干什么
  console.log("aaaaaa", error.response.status);
  switch (error.response.status) {
    case 404:
      console.log("url信息有误")
      break;
    case 500:
      console.log("服务器有问题")
      break;
  
    default:
      console.log("未知错误")
      break;
  }
```

# 15登录功能

1.输入框没有内容不能点击

创建变量  并且给按钮添加disabled属性

```
// 1.创建一个变量用来控制按钮是否能点击
let btnbool=ref(true)

2.页面中按钮添加禁用属性
   <el-button
            @click="submitForm(ruleFormRef)"
            type="danger"
            class="login-btn block"
            :disabled="btnbool"
            >{{ model === "login" ? "登录" : "注册" }}</el-button
          >
```

2.使用watch监听数据  判断输入框是否有值

````js

// 1.创建一个变量用来控制按钮是否能点击
let btnbool=ref(true)

watch(ruleForm,(newval)=>{
  console.log(newval)
  // 判断是登录还是注册
  if(model.value=='login'){
    // 登录
    if(newval.username!=""&&newval.password!=""){
      btnbool.value=false
    }else{
       btnbool.value=true
    }
  }else{
    // 注册
      if(newval.username!=""&&newval.password!=""&&newval.passwords!=""){
      btnbool.value=false
    }else{
       btnbool.value=true
    }
  }
})
````

3.发送请求

```js
const submitForm = (formEl: FormInstance | undefined) => {
  if (!formEl) return;
  formEl.validate((valid) => {
    if (valid) {
      // 判断是登录还是注册
      if (model.value == "login") {
        console.log("登录");
        // 登录请求发送

       
        link(`/register?uname=${ruleForm.username}&pwd=${ruleForm.password}`,"get").then(ok=>{
          // console.log(ok)
          let {data}=ok;//解构出数据
          // 判断data长度不为0登录成功
          if(data.length!=0){
            console.log("登录成功")
          }else{
            console.log("登录失败")
          }

        })

        


      } else {
        // 把要发送的数据拼装成一个对象
        let data = {
          uname: ruleForm.username,
          pwd: ruleForm.password,
        };

        link("/register", "POST", data).then((ok) => {
          ElMessage.error("注册失败");
          // 判断数据是否为空 不为空表示注册成功
          let { data } = ok;
          // 转成成数组判断长度即可知道对象是否为空
          if (Object.keys(data).length !== 0) {
            ElMessage("注册成功");
          //  把输入框的内容切换到登录
            model.value="login"
            // 把上面的切换按钮编程登录
            // 先把所有的的控制切换的变量编程false
              menuData.forEach((elem) => {
                elem.current = false;
              });
              // 在吧登录的编程true
              menuData[0].current=true;

           
          } else {
            ElMessage.error("注册失败");
          }
        });
      }
    } else {
      console.log("error submit!");
      return false;
    }
  });
};
```



# 16 自定义HOOK封装密码加密

本质上HOOK是一个函数  **只是把原来setup中我们写的组合式API进行了封装**（就是把原来需要重复的逻辑封装起来方便复用）

**类似于vue2的mixins**  方便的把多个组件需要重复使用的逻辑封装起来

1.下载md5插件    npm install js-md5 -D



2.新建一个hooks的文件夹用来容纳 把原来的逻辑复制过来  **但是不要忘了return数据**

```js
import md5 from 'js-md5'
import {ref} from "vue"
export default function(data){
    let mdData=ref(md5(data))//加密数据
    return mdData
}
```

3.在想使用的页面引用

```js
1.引用
import useMd5 from "../../hook/useMd5.js"

2.在注册的时候 使用hook来加密密码
 				let data = {
          uname: ruleForm.username,
          pwd: useMd5(ruleForm.password).value,
        };
        
3.在登录的时候 使用hook来加密密码    
 link(`/register?uname=${ruleForm.username}&pwd=${useMd5(ruleForm.password).value}`,"get")
```

# 17.useRouter导航

1.创建首页路由页面并且配置路由规则

```vue
<template>
  <div>
      首页
  </div>
</template>

<script setup>

</script>

<style>

</style>
```

配置首页路由规则

```js
import { createRouter, createWebHistory, RouteRecordRaw } from 'vue-router'


const routes: Array<RouteRecordRaw> = [
  {
    path: '/',
    redirect:"/login"
  },
  {
    path: '/login',
    name: 'login',
  
    component: () => import('../views/login/index.vue')
  },
  // 首页路由
  {
    path: '/home',
    name: 'home',
  
    component: () => import('../views/HomeView/index.vue')
  }
]

const router = createRouter({
  history: createWebHistory(process.env.BASE_URL),
  routes
})

export default router

```



2.登陆成功后跳转到首页

```js
1.引用
import {useRouter} from "vue-router"
let router=useRouter()

2.在登录成功使用编程式导航
  link(`/register?uname=${ruleForm.username}&pwd=${useMd5(ruleForm.password).value}`,"get").then(ok=>{
          // console.log(ok)
          let {data}=ok;//解构出数据
          // 判断data长度不为0登录成功
          if(data.length!=0){
            console.log("登录成功")

            // 编程式导航跳转
            router.push("/home")
            
          }else{
            console.log("登录失败")
          }

        })
```

# 18首页创建

1.首先我们的首页是一个左右布局 所以来到elementuiplus官网中来进行布局设置

1.找到布局容器  并且找到对应效果

2.注入到 首页页面中

````vue
<template>
  <div class="common-layout">
    <el-container>
      <el-aside width="200px">Aside</el-aside>
      <el-container>
        <el-header>Header</el-header>
        <el-main>Main</el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script setup>

</script>

<style>

</style>
````

3.设置背景颜色区分区块

```vue
<template>
  <div class="common-layout">
    <el-container>
      <el-aside width="200px">Aside</el-aside>
      <el-container>
        <el-header>Header</el-header>
        <el-main>Main</el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script setup>

</script>

<style lang="scss">
.common-layout{
    .el-aside{
        background-color: pink;
    }
    .el-header{
        background-color: gold;
    }
    .el-main{
        background-color: burlywood;
    }
}
</style>
```

3 高度自适应

```vue
<template>
  <div class="common-layout">
    <el-container>
      <el-aside width="200px">Aside</el-aside>
      <el-container>
        <el-header>Header</el-header>
        <el-main>Main</el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script setup>

</script>

<style lang="scss">
.common-layout{
    .el-aside{
        background-color: pink;
    }
    .el-header{
        background-color: gold;
    }
    .el-main{
        background-color: burlywood;
    }
}
// 高度100%
.el-aside,.el-container,.common-layout,#app,body,html{
    height: 100%;
}
</style>
```

 # 19elementui-plus--Menu导航

1.在homeview文件夹下创建components文件夹并且创建文件用来容纳左侧导航

创建首页左侧导航

```vue
<template>
  
      <el-menu
        active-text-color="#ffd04b"
        background-color="#545c64"
        class="el-menu-vertical-demo"
        default-active="2"
        text-color="#fff"
        @open="handleOpen"
        @close="handleClose"
      >
        <el-sub-menu index="1">
          <template #title>
            <el-icon><location /></el-icon>
            <span>Navigator One</span>
          </template>
          <el-menu-item-group title="Group One">
            <el-menu-item index="1-1">item one</el-menu-item>
            <el-menu-item index="1-2">item one</el-menu-item>
          </el-menu-item-group>
          <el-menu-item-group title="Group Two">
            <el-menu-item index="1-3">item three</el-menu-item>
          </el-menu-item-group>
          <el-sub-menu index="1-4">
            <template #title>item four</template>
            <el-menu-item index="1-4-1">item one</el-menu-item>
          </el-sub-menu>
        </el-sub-menu>
        <el-menu-item index="2">
          <el-icon><icon-menu /></el-icon>
          <span>Navigator Two</span>
        </el-menu-item>
        <el-menu-item index="3" disabled>
          <el-icon><document /></el-icon>
          <span>Navigator Three</span>
        </el-menu-item>
        <el-menu-item index="4">
          <el-icon><setting /></el-icon>
          <span>Navigator Four</span>
        </el-menu-item>
      </el-menu>
 
</template>

<script lang="ts" setup>
import {
  Document,
  Menu as IconMenu,
  Location,
  Setting,
} from '@element-plus/icons-vue'
const handleOpen = (key: string, keyPath: string[]) => {
  console.log(key, keyPath)
}
const handleClose = (key: string, keyPath: string[]) => {
  console.log(key, keyPath)
}
</script>
```

2.在首页中引用使用

```vue
<template>
  <div class="common-layout">
    <el-container>
      <el-aside width="200px">
          <!-- 2.使用组件 -->
          <Ln/>
      </el-aside>
      <el-container>
        <el-header>Header</el-header>
        <el-main>Main</el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script setup>
// 1.引用组件
    import Ln from "./components/LeftNav.vue"
</script>

<style lang="scss">
.common-layout{
    .el-aside{
        background-color: pink;
    }
    .el-header{
        background-color: gold;
    }
    .el-main{
        background-color: burlywood;
    }
}
// 高度100%
.el-aside,.el-container,.common-layout,#app,body,html{
    height: 100%;
}
</style>
```

# 20导航折叠的菜单

1.创建左侧顶部菜单组件

```vue
<template>
  <div>
      我是右侧头部组件
  </div>
</template>

<script>
export default {

}
</script>

<style>

</style>
```



2.在首页中引用使用

```vue
<template>
  <div class="common-layout">
    <el-container>
      <el-aside width="200px">
          <!-- 2.使用组件 -->
          <Ln/>
      </el-aside>
      <el-container>
        <el-header>
            <Tr/>
        </el-header>
        <el-main>Main</el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script setup>
// 1.引用组件
    import Ln from "./components/LeftNav.vue"
    import Tr from "./components/TopRight.vue"
</script>

<style lang="scss">
.common-layout{
    .el-aside{
        background-color: pink;
    }
    .el-header{
        background-color: gold;
    }
    .el-main{
        background-color: burlywood;
    }
}
// 高度100%
.el-aside,.el-container,.common-layout,#app,body,html{
    height: 100%;
}
</style>
```



3.在头部组件中设置点击图标用来切换导航 并设置图标样式

```vue
<template>
  <div>
    <!-- 2.使用图标 -->
    <el-icon><caret-right /></el-icon>
  </div>
</template>

<script lang="ts" setup>
// 1.引用图标
import { CaretRight } from "@element-plus/icons-vue";
</script>

<style lang="scss">
.el-header{
    line-height: 70px;//设置图标垂直居中
    .el-icon{
        font-size:20px;//设置图标大小
    }
}
</style>
```



4在vuex中创建模块 用来设置点击图标后切换导航的布尔值

在store下新建module文件夹用来容纳首页的vuex模块

```js
let homeview:Object={
    state: {
        navBool:false
    },
    getters: {
    },
    mutations: {
    },
    actions: {
    },
}
export default homeview;
```

在vuex的index文件中引用使用模块

```js
import { createStore } from 'vuex'
// 1.引用
import homeview from "./module/homeview"
export default createStore({
  state: {
  },
  getters: {
  },
  mutations: {
  },
  actions: {
  },
  modules: {
    homeview//使用模块
  }
})

```



4.给图标设置点击事件 从而修改vuex的布尔值 在真假中切换

```vue
<template>
  <div>
    <!-- 2.使用图标 -->
    <el-icon @click="ck"><caret-right /></el-icon>
  </div>
</template>

<script lang="ts" setup>
// 1.引用图标
import { CaretRight } from "@element-plus/icons-vue";

let ck=()=>{
    console.log("我被点击了")
}
</script>

<style lang="scss">
.el-header{
    line-height: 70px;//设置图标垂直居中
    .el-icon{
        font-size:20px;//设置图标大小
    }
}
</style>
```

# 21 Vuex--useStore

1.引用useStore  并且调用commit来进行数据的修改

```vue
<template>
  <div>
    <!-- 使用图标 -->
    <el-icon @click="ck"><caret-right /></el-icon>
  </div>
</template>

<script lang="ts" setup>
// 引用图标
import { CaretRight } from "@element-plus/icons-vue";
// 引用useStore
import { useStore } from "vuex";
// 得到store对象
const store = useStore();

let ck=()=>{
    // 触发mutations修改
    store.commit("SET_NAVBOOL")
}
</script>

<style lang="scss">
.el-header{
    line-height: 70px;//设置图标垂直居中
    .el-icon{
        font-size:20px;//设置图标大小
    }
}
</style>
```

2.创建对应的mutations

````js
let homeview:Object={
    state: {
        navBool:true
    },
    getters: {
    },
    mutations: {
        // 修改state的数据
        SET_NAVBOOL(state:any){
            state.navBool=!state.navBool
        }
    },
    actions: {
    },
}
export default homeview;
````

3.在页面中添加相反的箭头  用v-ifvuex的数据具体显示哪一个

```vue
<template>
  <div>
    <!-- 使用图标 -->
    <el-icon @click="ck">
        <caret-left v-if="$store.state.homeview.navBool"/>
        <caret-right v-else/>
    </el-icon>
  </div>
</template>

<script lang="ts" setup>
// 引用图标
import { CaretRight,CaretLeft } from "@element-plus/icons-vue";
// 引用useStore
import { useStore } from "vuex";
// 得到store对象
const store = useStore();

let ck=()=>{
    // 触发mutations修改
    store.commit("SET_NAVBOOL")
}
</script>

<style lang="scss">
.el-header{
    line-height: 70px;//设置图标垂直居中
    .el-icon{
        font-size:20px;//设置图标大小
    }
}
</style>
```

4.在左侧导航设置 collapse属性控制导航折叠

```
  <el-menu
        active-text-color="#ffd04b"
        background-color="#545c64"
        class="el-menu-vertical-demo"
        default-active="2"
        text-color="#fff"
        :collapse="$store.state.homeview.navBool"//设置导航折叠
        @open="handleOpen"
        @close="handleClose"
      >
```



5 导航是变了  但是右侧整体宽度不会随着页面的改变而变化  把左侧的宽度设置成auto即可自动改变

```
  <el-aside width="auto">
```



# 22 首页多级路由设置

首页下有

1.数据统计 EchartsView.vue

2.权限列表 PermissionList.vue

3.住户信息统计 userone.vue

（3-1）住户信息展示 userlist.vue

（3-2）住户信息修改 userupdate.vue



创建对应页面 与路由规则的配置

```js
import { createRouter, createWebHistory, RouteRecordRaw } from 'vue-router'


const routes: Array<RouteRecordRaw> = [
  {
    path: '/',
    redirect: "/login"
  },
  {
    path: '/login',
    name: 'login',

    component: () => import('../views/login/index.vue')
  },
  // 首页路由
  {
    path: '/home',
    name: 'home',

    component: () => import('../views/HomeView/index.vue'),
    // 设置二级路由
    children: [
      {
        path: '/echarts',
        name: 'echarts',
        component: () => import('../views/HomeChildren/EchartsView.vue')
      },
      {
        path: '/permissionlist',
        name: 'permissionlist',
        component: () => import('../views/HomeChildren/PermissionList.vue')
      },
      {
        path: "/user",
        name: "user",
        component: () => import("../views/HomeChildren/UserOne.vue"),
        redirect:"/userlist"
        children: [
          {
            path: '/userlist',
            name: 'userlist',
            component: () => import('../views/HomeChildren/UserList.vue')
          },
          {
            path: '/userupdate',
            name: 'userupdate',
            component: () => import('../views/HomeChildren/UserUpdate.vue'
          },
        ]
      }
    ]
  }
]

const router = createRouter({
  history: createWebHistory(process.env.BASE_URL),
  routes
})

export default router

```



设置路由出口

在homeview页面下右侧下方区域设置router-view路由出口   并且在userone.vue中设置路由出口



在页面中进行测试

# 23 路由实时路由获取

我们左侧的导航是根据路由规则实时获取动态展示 所以先把当前路由规则读取出来

在左侧导航

在leftnav.vue中获取当前路由信息

````js
<script lang="ts" setup>
import {
  Document,
  Menu as IconMenu,
  Location,
  Setting,
} from '@element-plus/icons-vue'

import {onMounted} from "vue"
// 获取路由信息
import { useRouter } from "vue-router";
const router = useRouter();
onMounted(()=>{
  console.log(router.options.routes)
})

// 获取路由信息

const handleOpen = (key: string, keyPath: string[]) => {
  console.log(key, keyPath)
}
const handleClose = (key: string, keyPath: string[]) => {
  console.log(key, keyPath)
}
</script>
````

设置路由标题与分类标题（因为有可能有二级菜单）

```js
import { createRouter, createWebHistory, RouteRecordRaw } from 'vue-router'


const routes: Array<RouteRecordRaw> = [
  {
    path: '/',
    redirect: "/login"
  },
  {
    path: '/login',
    name: 'login',

    component: () => import('../views/login/index.vue')
  },
  // 首页路由
  {
    path: '/home',
    name: 'home',

    component: () => import('../views/HomeView/index.vue'),
    // 设置二级路由
    children: [
      {
        path: '/echarts',
        name: 'echarts',
        component: () => import('../views/HomeChildren/EchartsView.vue'),
        meta: {
          title: "数据展示"
        }
      },
      {
        path: '/permissionlist',
        name: 'permissionlist',
        component: () => import('../views/HomeChildren/PermissionList.vue'),
        meta: {
          title: "权限列表"
        }
      },
      {
        path: "/user",
        name: "user",
        component: () => import("../views/HomeChildren/UserOne.vue"),
        redirect:"/userlist",
        meta: {
          title: "住户信息"
        },
        children: [
          {
            path: '/userlist',
            name: 'userlist',
            component: () => import('../views/HomeChildren/UserList.vue'),
            meta: {
              classifyTitle: "用户信息",//分类标题
              title: "住户列表"
            }
          },
          {
            path: '/userupdate',
            name: 'userupdate',
            component: () => import('../views/HomeChildren/UserUpdate.vue'),
            meta: {
              classifyTitle: "用户信息",//分类标题
              title: "住户信息修改"
            }
          },
        ]
      }
    ]
  }
]

const router = createRouter({
  history: createWebHistory(process.env.BASE_URL),
  routes
})

export default router

```



修改左侧列表删除掉没有用的内容

```html
<template>
  <el-menu
    active-text-color="#ffd04b"
    background-color="#545c64"
    class="el-menu-vertical-demo"
    default-active="2"
    text-color="#fff"
    :collapse="$store.state.homeview.navBool"
    @open="handleOpen"
    @close="handleClose"
  >
  
    <!-- 带下拉的导航 -->
    <el-sub-menu index="1">
      <template #title>
        <el-icon><location /></el-icon>
        <span>Navigator One</span>
      </template>
      <el-menu-item-group>
        <el-menu-item index="1-1">item one</el-menu-item>
        <el-menu-item index="1-2">item one</el-menu-item>
      </el-menu-item-group>
    </el-sub-menu>

      <!-- 不带下拉的列表 -->
        <el-menu-item index="4">
          <el-icon><setting /></el-icon>
          <span>Navigator Four</span>
        </el-menu-item>
  </el-menu>


</template>
```



3.开始遍历之前得到的路由信息

```vue
<template>
  <el-menu
    active-text-color="#ffd04b"
    background-color="#545c64"
    class="el-menu-vertical-demo"
    default-active="2"
    text-color="#fff"
    :collapse="$store.state.homeview.navBool"
    @open="handleOpen"
    @close="handleClose"
  >
  <!-- 循环路由数据   并且判断是否有二级菜单 -->
  <template v-for="(v,i) in router.options.routes[2].children" :key="v.path">
    <el-sub-menu index="1" v-if="v.children">
      <template #title>
        <el-icon><location /></el-icon>
        <span>Navigator One</span>
      </template>
      <el-menu-item-group>
        <el-menu-item index="1-1">item one</el-menu-item>
        <el-menu-item index="1-2">item one</el-menu-item>
      </el-menu-item-group>
    </el-sub-menu>

    <!-- 不带下拉的列表 -->
    <el-menu-item index="4" v-else>
      <el-icon><setting /></el-icon>
      <span>Navigator Four</span>
    </el-menu-item>

    </template>
  </el-menu>
</template>
```

4添加  展示数据

```vue
<template>
  <el-menu
    active-text-color="#ffd04b"
    background-color="#545c64"
    class="el-menu-vertical-demo"
    default-active="2"
    text-color="#fff"
    :collapse="$store.state.homeview.navBool"
    @open="handleOpen"
    @close="handleClose"
  >
  <!-- 循环路由数据   并且判断是否有二级菜单 -->
  <template v-for="(v,i) in router.options.routes[2].children" :key="v.path">
    <el-sub-menu index="1" v-if="v.children">
      <template #title>
        <el-icon><location /></el-icon>
        <!-- 添加展示数据 -->
        <span>{{v.meta.title}}</span>
      </template>
      <el-menu-item-group>
        <el-menu-item index="1-1">item one</el-menu-item>
        <el-menu-item index="1-2">item one</el-menu-item>
      </el-menu-item-group>
    </el-sub-menu>

    <!-- 不带下拉的列表 -->
    <el-menu-item index="4" v-else>
      <el-icon><setting /></el-icon>
      <!-- 添加展示数据 -->
      <span>{{v.meta.title}}</span>
    </el-menu-item>

    </template>
  </el-menu>
</template>
```



5生成二级菜单

```vue
<template>
  <el-menu
    active-text-color="#ffd04b"
    background-color="#545c64"
    class="el-menu-vertical-demo"
    default-active="2"
    text-color="#fff"
    :collapse="$store.state.homeview.navBool"
    @open="handleOpen"
    @close="handleClose"
  >
  <!-- 循环路由数据   并且判断是否有二级菜单 -->
  <template v-for="(v,i) in router.options.routes[2].children" :key="v.path">
    <el-sub-menu index="1" v-if="v.children">
      <template #title>
        <el-icon><location /></el-icon>
        <!-- 添加展示数据 -->
        <span>{{v.meta.title}}</span>
      </template>
      <!-- 循环二级菜单 -->
      <el-menu-item-group v-for="(val,index) in v.children" :key="val.path">
        <el-menu-item index="1-1">{{val.meta.title}}</el-menu-item>
  
      </el-menu-item-group>
    </el-sub-menu>

    <!-- 不带下拉的列表 -->
    <el-menu-item index="4" v-else>
      <el-icon><setting /></el-icon>
      <!-- 添加展示数据 -->
      <span>{{v.meta.title}}</span>
    </el-menu-item>

    </template>
  </el-menu>
</template>
```

6设置导航

```vue
 <el-menu
    active-text-color="#ffd04b"
    background-color="#545c64"
    class="el-menu-vertical-demo"
    default-active="2"
    text-color="#fff"
    :collapse="$store.state.homeview.navBool"
    @open="handleOpen"
    @close="handleClose"
    router
  >
  <!-- 添加router属性 就是element提供的根据列表的index属性当成页面跳转路径 -->
```

在导航中也设置index属性的值为path路径从而完成页面的跳转

```vue
<template>
  <el-menu
    active-text-color="#ffd04b"
    background-color="#545c64"
    class="el-menu-vertical-demo"
    default-active="2"
    text-color="#fff"
    :collapse="$store.state.homeview.navBool"
    @open="handleOpen"
    @close="handleClose"
    router
  >
  <!-- 添加router属性 就是element提供的根据列表的index属性当成页面跳转路径 -->
  <!-- 循环路由数据   并且判断是否有二级菜单 -->
  <template v-for="(v) in router.options.routes[2].children" :key="v.path">
   <!-- 111111111111111设置index为path路径 -->
    <el-sub-menu :index="v.path" v-if="v.children">
      <template #title>
        <el-icon><location /></el-icon>
        <!-- 添加展示数据 -->
        <span>{{v.meta.title}}</span>
      </template>
      <!-- 循环二级菜单 -->
      <el-menu-item-group v-for="(val) in v.children" :key="val.path">
      <!-- 111111111111设置index为path路径 -->
        <el-menu-item :index="val.path">{{val.meta.title}}</el-menu-item>
  
      </el-menu-item-group>
    </el-sub-menu>

    <!-- 不带下拉的列表 -->
     <!-- 1111111111设置index为path路径 -->
    <el-menu-item :index="v.path" v-else>
      <el-icon><setting /></el-icon>
      <!-- 添加展示数据 -->
      <span>{{v.meta.title}}</span>
    </el-menu-item>

    </template>
```

宽度有问题设置下宽度

```vue
<template>
  <div class="common-layout">
    <el-container>
      <!-- 设置宽度 -->
      <el-aside :width="$store.state.homeview.navBool">
          <!-- 2.使用组件 -->
          <Ln/>
      </el-aside>
      <el-container>
        <el-header>
            <Tr/>
        </el-header>
        <el-main>
          <!-- 路由出口设置 -->
          <router-view></router-view>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>
```

# 24 住户信息列表



1 获取到elementplus的表格到我们页面当中userlist.vue

```js
<template>
  <el-table :data="tableData" style="width: 100%">
    <el-table-column prop="date" label="Date" width="180" />
    <el-table-column prop="name" label="Name" width="180" />
    <el-table-column prop="address" label="Address" />
  </el-table>
</template>

<script lang="ts" setup>
const tableData = [
  {
    date: '2016-05-03',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-02',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-04',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
]
</script>

<style>

</style>
```



2.增加点数据之后发现数据会把页面撑大  所以我们要进行分页处理



3.设置分页  找到带附加功能的分页 并且使用All combined这个分页项

````vue
<template>
  <el-table :data="tableData" style="width: 100%">
    <el-table-column prop="date" label="Date" width="180" />
    <el-table-column prop="name" label="Name" width="180" />
    <el-table-column prop="address" label="Address" />
  </el-table>

  <!-- 设置导航 -->

   <el-pagination
      v-model:currentPage="currentPage4"
      v-model:page-size="pageSize4"
      :page-sizes="[100, 200, 300, 400]"
      :small="small"
      :disabled="disabled"
      :background="background"
      layout="total, sizes, prev, pager, next, jumper"
      :total="400"
      @size-change="handleSizeChange"
      @current-change="handleCurrentChange"
    />

</template>

<script lang="ts" setup>
import {ref} from "vue"
// 设置需要的参数与方法
const currentPage4 = ref(4)
const pageSize4 = ref(100)
const handleSizeChange = (val: number) => {
  console.log(`${val} items per page`)
}
const handleCurrentChange = (val: number) => {
  console.log(`current page: ${val}`)
}




const tableData = [
  {
    date: '2016-05-03',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-02',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-04',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
]
</script>

<style>

</style>
````

4设置分页属性  与方法

```js
<template>
  <el-table :data="tableData" style="width: 100%">
    <el-table-column prop="date" label="Date" width="180" />
    <el-table-column prop="name" label="Name" width="180" />
    <el-table-column prop="address" label="Address" />
  </el-table>

  <!-- 设置导航 -->
  <!-- 修改下面得属性 -->
   <el-pagination
   
      layout="total, sizes, prev, pager, next, jumper"
      :total="tableData.length"
      @size-change="handleSizeChange"
      @current-change="handleCurrentChange"
      :current-page="currentPage4.value"
    />

</template>

<script lang="ts" setup>
import {ref} from "vue"
// 设置需要的参数与方法
const currentPage4 = ref(1)
const pageSize4 = ref(10)

// 修改下面得方法
const handleSizeChange = (val: number) => {
 //一页显示多少条

      pageSize4.value = val;
}
const handleCurrentChange = (val: number) => {
  //页码更改方法

      currentPage4.value = val;
}




const tableData = [
  {
    date: '2016-05-03',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-02',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-04',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
  {
    date: '2016-05-01',
    name: 'Tom',
    address: 'No. 189, Grove St, Los Angeles',
  },
]
</script>

<style>

</style>
```

5修改绑定的参数

```html
<el-table :data="tableData.slice((currentPage4 - 1) * pageSize4, currentPage4 * pageSize4) " style="width: 100%">
```

6修改表格宽度 

删除掉表格上面的width属性

    <el-table-column prop="date" label="Date"  />
    <el-table-column prop="name" label="Name" />

# 25住户信息列表查找

在表格顶部添加输入框（elementui  表格想相关设置）  并且使用计算属性处理数据

```vue
<template>
  <!-- 对数据进行截取 是当前页数-1 乘以 显示条数     当前页数乘以显示条数 -->
  <el-table
    :data="
      filterTableData.slice((currentPage4 - 1) * pageSize4, currentPage4 * pageSize4)
    "
    style="width: 100%"
  >
    <el-table-column prop="date" label="Date" />
    <el-table-column prop="name" label="Name" />
    <el-table-column prop="address" label="Address" />
<!-- 添加输入框 -->
    <el-table-column align="right">
      <template #header>
        <el-input v-model="search" size="small" placeholder="Type to search" />
      </template>
    </el-table-column>
<!-- 添加输入框 -->
  </el-table>

  <!-- 设置导航 -->
  <!-- 修改下面得属性 -->
  <el-pagination
    layout="total, sizes, prev, pager, next, jumper"
    :total="tableData.length"
    @size-change="handleSizeChange"
    @current-change="handleCurrentChange"
    :current-page="currentPage4"
  />
</template>

<script lang="ts" setup>
import { ref,computed } from "vue";
// 设置需要的参数与方法
const currentPage4 = ref(1);
const pageSize4 = ref(10);
const search = ref('')
// 使用计算属性处理数据
const filterTableData = computed(() =>
  tableData.filter(
    (data) =>
      !search.value ||
      data.name.toLowerCase().includes(search.value.toLowerCase())
  )
)

// 修改下面得方法
const handleSizeChange = (val: number) => {
  //一页显示多少条

  pageSize4.value = val;
};
const handleCurrentChange = (val: number) => {
  //页码更改方法

  currentPage4.value = val;
};

const tableData = [
  {
    date: "2016-05-03",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-02",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-04",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "aa",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "bb",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
];
</script>

<style>
</style>
```

# 26 住户信息修改

1.复用用户信息列表userlist组件内容到userupdate组件中

```vue
<template>
  <!-- 对数据进行截取 是当前页数-1 乘以 显示条数     当前页数乘以显示条数 -->
  <el-table
    :data="
      filterTableData.slice((currentPage4 - 1) * pageSize4, currentPage4 * pageSize4)
    "
    style="width: 100%"
  >
    <el-table-column prop="date" label="Date" width="180" />
    <el-table-column prop="name" label="Name" width="180" />
    <el-table-column prop="address" label="Address" />
<!-- 添加输入框 -->
    <el-table-column align="right">
      <template #header>
        <el-input v-model="search" size="small" placeholder="Type to search" />
      </template>
    </el-table-column>
<!-- 添加输入框 -->
  </el-table>

  <!-- 设置导航 -->
  <!-- 修改下面得属性 -->
  <el-pagination
    layout="total, sizes, prev, pager, next, jumper"
    :total="tableData.length"
    @size-change="handleSizeChange"
    @current-change="handleCurrentChange"
    :current-page="currentPage4"
  />
</template>

<script lang="ts" setup>
import { ref,computed } from "vue";
// 设置需要的参数与方法
const currentPage4 = ref(1);
const pageSize4 = ref(10);
const search = ref('')
// 使用计算属性处理数据
const filterTableData = computed(() =>
  tableData.filter(
    (data) =>
      !search.value ||
      data.name.toLowerCase().includes(search.value.toLowerCase())
  )
)

// 修改下面得方法
const handleSizeChange = (val: number) => {
  //一页显示多少条

  pageSize4.value = val;
};
const handleCurrentChange = (val: number) => {
  //页码更改方法

  currentPage4.value = val;
};

const tableData = [
  {
    date: "2016-05-03",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-02",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-04",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "aa",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "bb",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
  {
    date: "2016-05-01",
    name: "Tom",
    address: "No. 189, Grove St, Los Angeles",
  },
];
</script>

<style>
</style>
```



2添加删除和修改的按钮从element找

```vue
<template>
 ........
 
    <el-table-column align="right">
      <template #header>
        <el-input v-model="search" size="small" placeholder="Type to search" />
      </template>
    </el-table-column>


    <!-- 添加删除和修改按钮 -->
    <el-table-column>
      <template #default="scope">
        <el-button size="small" @click="handleEdit(scope.$index, scope.row)"
          >Edit</el-button
        >
        <el-button
          size="small"
          type="danger"
          @click="handleDelete(scope.$index, scope.row)"
          >Delete</el-button
        >
      </template>
    </el-table-column>
    <!-- 添加删除和修改按钮 -->
  </el-table>


  <el-pagination
    layout="total, sizes, prev, pager, next, jumper"
    :total="tableData.length"
    @size-change="handleSizeChange"
    @current-change="handleCurrentChange"
    :current-page="currentPage4"
  />
</template>

<script lang="ts" setup>
import { ref, computed } from "vue";
.........

const handleSizeChange = (val: number) => {
  pageSize4.value = val;
};
const handleCurrentChange = (val: number) => {
  currentPage4.value = val;
};

// 添加删除和修改按钮方法与接口
interface User {
  date: string;
  name: string;
  address: string;
}
const handleEdit = (index: number, row: User) => {
  console.log(index, row);
};
const handleDelete = (index: number, row: User) => {
  console.log(index, row);
};
// 添加删除和修改按钮方法与接口

const tableData = [
.........
];
</script>

<style>
</style>
```

3 设置点击修改之后的输入弹框

在elementplus中的对话框 dialog中找到自定义内容

设置嵌套表单的弹出框

在components中新建 组件用来封装弹出框 UpdateDialog.vue

```vue
<template>
  
  <el-dialog v-model="dialogFormVisible" title="Shipping address">
    <el-form :model="form">
      <el-form-item label="Promotion name" :label-width="formLabelWidth">
        <el-input v-model="form.name" autocomplete="off" />
      </el-form-item>
      <el-form-item label="Zones" :label-width="formLabelWidth">
        <el-select v-model="form.region" placeholder="Please select a zone">
          <el-option label="Zone No.1" value="shanghai" />
          <el-option label="Zone No.2" value="beijing" />
        </el-select>
      </el-form-item>
    </el-form>
    <template #footer>
      <span class="dialog-footer">
        <el-button @click="dialogFormVisible = false">Cancel</el-button>
        <el-button type="primary" @click="dialogFormVisible = false"
          >Confirm</el-button
        >
      </span>
    </template>
  </el-dialog>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue'

const dialogTableVisible = ref(false)
const dialogFormVisible = ref(false)
const formLabelWidth = '140px'

const form = reactive({
  name: '',
  region: '',
  date1: '',
  date2: '',
  delivery: false,
  type: [],
  resource: '',
  desc: '',
})

</script>

<style scoped>
.el-button--text {
  margin-right: 15px;
}
.el-select {
  width: 300px;
}
.el-input {
  width: 300px;
}
.dialog-footer button:first-child {
  margin-right: 10px;
}
</style>
```

4.把封装的组件在userupdate中引用 使用

5.分析代码 发现当点击之后需要设置一个变量的改变控制弹出框 但是不同组件  所以使用vuex来进行这个变量的状态共享

vuex中创建state

```
 state: {
        navBool:false,
        // 创建控制弹出框的状态
        dialogFormVisible:false
    },
```



在页面的修改按钮上绑定事件点击之后修改这个状态

```js
//页面引用
// 引用useStore
import { useStore } from "vuex";
// 得到store对象
const store = useStore();


//在组件的修改按钮调用函数中添加commit
const handleEdit = (index: number, row: User) => {
  console.log(index, row);
  // 调用vuex修改
  store.commit("SET_DIALOG")
};
```

创建mutations

```js
 mutations: {
        // 修改state的数据
        SET_NAVBOOL(state:any){
            state.navBool=!state.navBool
        },
        // 修改
        SET_DIALOG(state:any){
            state.dialogFormVisible=!state.dialogFormVisible
        }
    },
```

在弹出框上绑定变量状态

```html
<el-dialog v-model="$store.state.homeview.dialogFormVisible" title="Shipping address">
```



在修改弹出框的两个按钮 点击之后关闭弹出框

```vue
<template>
  
  <el-dialog v-model="$store.state.homeview.dialogFormVisible" title="Shipping address">
    <el-form :model="form">
      <el-form-item label="Promotion name" :label-width="formLabelWidth">
        <el-input v-model="form.name" autocomplete="off" />
      </el-form-item>
      <el-form-item label="Zones" :label-width="formLabelWidth">
        <el-select v-model="form.region" placeholder="Please select a zone">
          <el-option label="Zone No.1" value="shanghai" />
          <el-option label="Zone No.2" value="beijing" />
        </el-select>
      </el-form-item>
    </el-form>
    <template #footer>
      <span class="dialog-footer">
          <!-- 绑定函数 -->
        <el-button @click="toggleDialog()">Cancel</el-button>
        <el-button type="primary" @click="toggleDialog()"
          >Confirm</el-button
        >
      </span>
    </template>
  </el-dialog>
</template>

<script setup lang="ts">
import { reactive, ref } from 'vue'

// 引用useStore
import { useStore } from "vuex";
// 得到store对象
const store = useStore();

const dialogTableVisible = ref(false)
const dialogFormVisible = ref(false)
const formLabelWidth = '140px'

const form = reactive({
.....
})

let toggleDialog=()=>{
  // 调用vuex修改
  store.commit("SET_DIALOG")
}

</script>

<style scoped>
......
</style>
```

6修改弹出框样式(内容)

```vue
<template>
  
  <el-dialog v-model="$store.state.homeview.dialogFormVisible" title="请输入修改内容">
    <el-form :model="form">
      <el-form-item label="姓名" :label-width="formLabelWidth">
        <el-input v-model="form.name" autocomplete="off" />
      </el-form-item>
      <el-form-item label="详细地址" :label-width="formLabelWidth">
     
          <el-input v-model="form.region" autocomplete="off" />
      </el-form-item>
    </el-form>
    <template #footer>
      <span class="dialog-footer">
          <!-- 绑定函数 -->
        <el-button @click="toggleDialog()">取消</el-button>
        <el-button type="primary" @click="toggleDialog()"
          >确定</el-button
        >
      </span>
    </template>
```

修改每隔elform-item上的label-wath属性到 el-from上

```
<el-form :model="form" :label-width="formLabelWidth">
```

修改输入框宽度

注释掉默认样式

```

  
  <style scoped>
.el-button--text {
  margin-right: 15px;
}
.el-select {
  width: 300px;
}
/* .el-input {
  width: 300px;
} */
.dialog-footer button:first-child {
  margin-right: 10px;
}
</style>
```



开始修改

当点击确定按钮时候调用函数并且在函数中得到修改的输入框的值

1.修改输入框的类型 和绑定的变量

```
    <el-form-item label="姓名" prop="name">
      <el-input v-model="form.name" autocomplete="off" />
    </el-form-item>
```

2.在函数中得到输入框的值

```js
let toggleDialog=()=>{
  store.commit("SET_DIALOG")
//   得到输入框的值
console.log(form.name+"---"+form.region)
}

```

3.但是这个方法确定和取消都在用  所以我们传递一个形参 来辨别用户到底点击了那个

```vue
 <el-button @click="toggleDialog(0)">取消</el-button>
 <el-button type="primary" @click="toggleDialog(1)">确定</el-button>


let toggleDialog = (num: Number) => {
  store.commit("SET_DIALOG");

  if (num == 0) {
    //   用户点击了取消
  } else {
    //   用户点击了确定
    //   得到输入框的值
    console.log(form.name + "---" + form.region);
  }
};
```



设置表格数据在vuex中

因为我们要对展示数据进行操纵 所以把原有写在组件中的表格数据放到vuex中

````
 state: {
        navBool:false,
        // 创建控制弹出框的状态
        dialogFormVisible:false,
        tableData :[
            {
              date: "2016-05-03",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-02",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-04",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-01",
              name: "aa",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-01",
              name: "bb",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-01",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-01",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-01",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-01",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-01",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-01",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-01",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-01",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-01",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-01",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-01",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-01",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-01",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-01",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-01",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-01",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
            {
              date: "2016-05-01",
              name: "Tom",
              address: "No. 189, Grove St, Los Angeles",
            },
          ]
````

把表格的数据从vuex中获取

```vue
<template>
 。。。。。
  <el-pagination
    layout="total, sizes, prev, pager, next, jumper"
     <!-- 修改下面从vuex读取 -->
    :total="$store.state.homeview.tableData.length"
    @size-change="handleSizeChange"
    @current-change="handleCurrentChange"
    :current-page="currentPage4"
  />

  <!-- 弹出框组件 -->
  <Ud/>
</template>

<script lang="ts" setup>
。。。
// 修改下面从vuex读取
const filterTableData = computed(() =>
  store.state.homeview.tableData.filter(
    (data) =>
      !search.value ||
      data.name.toLowerCase().includes(search.value.toLowerCase())
  )
);
...........

</script>

<style>
</style>
```

