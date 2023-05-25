---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: '/background.jpg'
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# persist drawings in exports and build
drawings:
  persist: false
# page transition
transition: slide-left
# use UnoCSS
css: unocss
# 字体
fonts:
  # 基础字体
  sans: 'ZCOOL KuaiLe, ZCOOL QingKe HuangYou, Kanit'
  # 与 windicss 的 `font-serif` css 类一同使用
  serif: 'Robot Slab'
  # 用于代码块、内联代码等
  mono: 'Fira Code'
hideInToc: true
---
# Debug Tricks
一些代码调试相关的小技巧
<p class="presenter">Yuting Huang</p>

<style>
.presenter {
  position: absolute;
  right: 50px;
  bottom: 10px;
  opacity: 0.3;
}
</style>
---
transition: fade-out
hideInToc: true
---
# Debug过程中，你是否遇到过这些烦恼？
<br />
<p v-click>我明明给两个元素设置了一样的height，可肉眼看上去，它们就是没有对齐，也不知道那1px到底差在了哪里？</p>
<br />
<p v-click>刚接手了一个不大熟悉的系统，页面上明明显示了那几个字啊，可是代码中怎么也搜不到，还要一点点读那些祖传的<svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 512 512"><path fill="#888888" d="M117.834 17.443c42.376 107.05-62.124 114.634 20.678 210.897c-28.655-84.62 51.3-129.568-20.678-210.897zm225.922.688c-2.024-.06-4.103.345-6.365 1.25c-5.17 2.064-11.69 7.488-18.13 18.643c-6.44 11.155-9.613 22.672-9.77 31.35c-.156 8.68 2.39 13.3 5.285 14.973c2.895 1.67 8.17 1.564 15.608-2.91c7.437-4.475 15.823-12.98 22.263-24.135c6.44-11.154 7.88-19.51 7.083-25.023c-.8-5.512-3.368-8.892-8.162-11.66c-2.397-1.384-4.648-2.21-6.947-2.43c-.286-.03-.575-.047-.864-.056zm50.674 45.04c-.41.01-.833.028-1.266.06c-5.198.37-11.99 2.385-20.357 7.215c-11.156 6.442-19.662 14.83-24.137 22.266c-4.475 7.438-4.58 12.713-2.908 15.608c1.67 2.895 6.292 5.44 14.97 5.284c8.68-.157 20.195-3.33 31.35-9.77c11.153-6.44 16.58-12.956 18.645-18.13c2.065-5.172 1.528-9.384-1.24-14.177c-2.767-4.793-6.146-7.364-11.657-8.162a20.557 20.557 0 0 0-3.4-.193zm42.797 9.816c-35.587 150.27 34.9 124.747 10.625 263.5c57.687-113.445-1.726-153.902-10.625-263.5zM311.852 101.52c-6.42-.166-12.73 3.096-16.166 9.05c-5 8.66-2.034 19.733 6.627 24.733c8.66 5 19.732 2.033 24.732-6.627s2.033-19.733-6.627-24.733a18.041 18.041 0 0 0-8.566-2.422zm-84.47 18.8c-58.445 21.166-65.416 76.894-51.294 117.698c10.148 12.91 56.414 25.582 56.414 25.582s-48.184-7.06-63.832-7.315v-.002l.027-.08c-38.84 4.528-68.547 27.707-68.547 55.518c0 7.123 1.957 13.93 5.51 20.19c11.354 13.146 82.012 29.77 82.012 29.77s-71.235-10.798-88.484-11.4c-45.124 6.186-79.426 35.19-79.426 69.91c0 39.206 43.726 70.87 97.394 70.87h275.508c53.67 0 97.014-31.664 97.014-70.87c0-39.203-43.344-71.147-97.014-71.147h-1.607c12.914-9.91 20.763-22.974 20.763-37.322c0-29.684-33.554-54.095-76.207-56.17c28.615-95.79-135.14-67.4-108.232-135.23zM60.54 148.885c-87.533 77.6 24.97 64.76-4.636 186.05c59.073-112.215-31.264-111.346 4.635-186.05z"/></svg><svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 15 15"><path fill="#888888" d="M7.5 1c-.3 0-.4.2-.6.4l-5.8 9.5c-.1.1-.1.3-.1.4c0 .5.4.7.7.7h11.6c.4 0 .7-.2.7-.7c0-.2 0-.2-.1-.4L8.2 1.4C8 1.2 7.8 1 7.5 1zm0 1.5L10.8 8H10L8.5 6.5L7.5 8l-1-1.5L5 8h-.9z"/></svg>，哎哟真难受……</p>
<br />
<p v-click>打了断点后查bug，只能“下一步”“下一步”地走，一旦关键信息错过去了，就要从头再来，Chrome就不能开发个“上一步”的功能吗？</p>
<br />
<p v-click>测试提了个bug，录屏的视频都发来了，可我这边死活都复现不出来，这个班真是一天都上不下去了……</p>
<img v-click src="/joke.png" class="rounded shadow" />

<style>
svg {
  display: inline-block;
}
svg:first-child {
  margin-bottom: 5px;
}
img {
  position: absolute;
  width: 400px;
  height: 400px;
  top: 50%;
  left: 50%;
  transform: translate(-200px, -200px) rotate(350deg);
}
</style>
---
transition: fade-out
hideInToc: true
---
# Table of contents
<br />
<Toc listClass="my-toc" />

<style>
:deep(.my-toc li) {
  margin-bottom: 20px;
}
</style>
---
transition: fade-out
---
# 巧用 CSS 轮廓 (outline) 属性
<div class="grid grid-cols-3">
  <div class="col-span-2">
    <div class="h-5" />
    <img src="/outline.png" class="rounded shadow" />
  </div>
  <div class="ml-20 -mt-5">
    <p class="underline">属性定义：</p>
    <p>绘制于元素周围的一条线，位于边框边缘的外围</p>
    <div class="h-1" />
    <p class="underline">使用场景：</p>
    <p>检测微小的布局偏差</p>
    <div class="h-1" />
    <p class="underline">演示案例：</p>
    <p>Admin系统 -【登录】页面 - 页脚部分</p>
  </div>
</div>
```css
  /* 新建样式规则 */
  * {
    outline: solid 1px;
  }
```
---
transition: fade-out
---
# 同时显示 /源代码/ 与 /控制台/
<br />
<div class="columns-2">
  <div>
    <img src="/show-console.png" class="rounded shadow" />
    <br />
    <p class="underline">快捷键：</p>
    <p>Esc</p>
  </div>
  <div>
    <img src="/hide-console.png" class="rounded shadow" />
    <br />
  </div>
</div>
<div class="h-3" />
<p class="underline">使用场景：</p>
<p>暂停程序代码后，实时编程测试运行的可能性，且无需切换标签页</p>
---
transition: fade-out
---
# 可简省代码的 Console API
<div class="h-1" />
<p><span class="clear-eng">【$_】</span>：获取最近一次的运行结果</p>
<p><span class="clear-eng">【$0】</span>：在Elements面板内选中元素后，在Console面板内通过它获取该元素</p>
<p><span class="clear-eng">【$1】~【$4】</span>：同上类推，获取前2~5次选中的元素</p>
<p><span class="clear-eng">【$】</span>：document.querySelector(selectors)，返回文档中与指定CSS选择器匹配的第一个元素</p>
<p><span class="clear-eng">【$$】</span>：document.querySelectorAll(selectors)</p>
<div class="h-1" />
<p class="underline">使用场景：</p>
<p>拆分代码语句，省略变量声明与执行结果存储</p>
<p class="underline">演示案例：</p>
<p>EDM系统 -【新建实验】页面 - 与Draw的交互功能</p>
---
transition: fade-out
---
# 如何筛选网络请求的结果
<br />
<div class="grid grid-cols-3">
  <div class="col-span-2">
    <img src="/network-filter.png" class="rounded shadow" />
  </div>
  <div class="ml-20 -mt-5">
    <p class="underline">快捷键：</p>
    <p>Ctrl + F</p>
    <div class="h-1" />
    <p class="underline">使用场景：</p>
    <p>未在源代码中查询到页面展示元素时</p>
    <div class="h-1" />
    <p class="underline">演示案例：</p>
    <p>SIP系统 - 菜单栏部分</p>
  </div>
</div>
---
transition: fade-out
---
# 调用堆栈中的 /重启帧/ 功能
<br />
<div class="grid grid-cols-3">
  <div class="col-span-2">
    <img src="/restart-frame.png" class="rounded shadow" />
  </div>
  <div class="ml-20 -mt-5">
    <div class="h-1" />
    <p class="underline">使用场景：</p>
    <p>在调试中途，重启之前的代码</p>
    <div class="h-1" />
    <p class="underline">演示案例：</p>
    <p>Report Builder插件 - 插入动态表格</p>
  </div>
</div>
---
transition: fade-out
---
# 手动模拟网速限制
<div class="h-5" />
<div class="columns-2">
  <img src="/network-throttling.png" class="rounded shadow" />
  <div class="ml-20">
    <p class="underline">使用场景：</p>
    <p>排查由于【加载数据时，未考虑响应延迟的情况】而引发的偶现的bug</p>
    <br />
    <p class="underline">演示案例：</p>
    <p>Admin系统 -【角色管理】页面 -【绑定菜单】弹窗</p>
  </div>
</div>
---
transition: fade-out
hideInToc: true
---
# 模拟网速限制 - 错误代码示例
<br />
```ts {1,2,3,5,7,8,10,15}
  // bindMenuModal.vue
  watch(visible, (val) => {
    if (val) setCheckedKeys();
    else checkedKeys.value = [];
  });

  async function setCheckedKeys() {
    const res = await rolesapi.getBindMenu(props.id);
    if (res.code === HttpStatus.success) {
      checkedKeys.value = res.rows;
    } else {
      checkedKeys.value = [];
      message.error(res.message);
    }
  }
```
---
transition: fade-out
---
# 一个关于“开发环境无法复现”的bug
<br />
<div class="columns-2">
  <img src="/bug34981.png" class="h-70 rounded shadow" />
  <img src="/bug34981-solve.png" class="ml-5 h-70 rounded shadow" />
</div>
<br />
<p>打破惯性思路，测试账号本身可能已经污染！</p>
