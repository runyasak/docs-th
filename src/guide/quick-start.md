---
footer: false
---

<script setup>
import { VTCodeGroup, VTCodeGroupTab } from '@vue/theme'
</script>

# เริ่มต้นใช้งานอย่างรวดเร็ว {#quick-start}

## ลองใช้ Vue ออนไลน์ {#try-vue-online}

- หากต้องการลองใช้งาน Vue อย่างรวดเร็ว คุณสามารถลองใช้ได้โดยตรงที่ [พื้นที่ทดลอง](https://play.vuejs.org/#eNo9jcEKwjAMhl/lt5fpQYfXUQfefAMvvRQbddC1pUuHUPrudg4HIcmXjyRZXEM4zYlEJ+T0iEPgXjn6BB8Zhp46WUZWDjCa9f6w9kAkTtH9CRinV4fmRtZ63H20Ztesqiylphqy3R5UYBqD1UyVAPk+9zkvV1CKbCv9poMLiTEfR2/IXpSoXomqZLtti/IFwVtA9A==).

- หากคุณชอบการตั้งค่า HTML แบบง่าย ๆ โดยไม่ต้องใช้การ build คุณสามารถใช้ [JSFiddle](https://jsfiddle.net/yyx990803/2ke1ab0z/) เป็นจุดเริ่มต้น

- หากคุณคุ้นเคยกับ Node.js และเครื่องมือ build อยู่แล้ว คุณสามารถลองใช้งานชุดการตั้งค่า build ได้ในเบราว์เซอร์ของคุณที่ [StackBlitz](https://vite.new/vue)

## การสร้างแอปพลิเคชัน Vue {#creating-a-vue-application}

:::tip ข้อกำหนดเบื้องต้น

- ความคุ้นเคยกับการใช้งาน command line
- ติดตั้ง [Node.js](https://nodejs.org/) เวอร์ชัน 18.3 หรือสูงกว่า
  :::

ในส่วนนี้ เราจะอธิบายวิธีการสร้างโครงสร้างพื้นฐานของ [Single Page Application](/guide/extras/ways-of-using-vue#single-page-application-spa) ด้วย Vue บนเครื่องของคุณ โครงการที่สร้างขึ้นจะใช้ชุดการตั้งค่าการ build ที่อิงกับ [Vite](https://vitejs.dev) และช่วยให้เราสามารถใช้งาน [Single-File Components](/guide/scaling-up/sfc) (SFCs) ได้

ตรวจสอบให้แน่ใจว่าคุณติดตั้ง [Node.js](https://nodejs.org/) เวอร์ชันล่าสุดและไดเรกทอรีที่คุณทำงานเป็นตำแหน่งที่คุณต้องการสร้างโปรเจ็กต์ ใช้คำสั่งต่อไปนี้ใน command line ของคุณ (ไม่รวม `$`):

<VTCodeGroup>
  <VTCodeGroupTab label="npm">

```sh
$ npm create vue@latest
```

  </VTCodeGroupTab>
  <VTCodeGroupTab label="pnpm">

```sh
$ pnpm create vue@latest
```

  </VTCodeGroupTab>
  <VTCodeGroupTab label="yarn">

```sh
# สำหรับ Yarn Modern (v2+)
$ yarn create vue@latest

# สำหรับ Yarn ^v4.11
$ yarn dlx create-vue@latest
```

  </VTCodeGroupTab>
  <VTCodeGroupTab label="bun">

```sh
$ bun create vue@latest
```

  </VTCodeGroupTab>
</VTCodeGroup>

คำสั่งนี้จะติดตั้งและเรียกใช้ [create-vue](https://github.com/vuejs/create-vue) ซึ่งเป็นเครื่องมือสร้างโครงสร้างโปรเจ็กต์อย่างเป็นทางการของ Vue คุณจะได้รับคำถามเกี่ยวกับฟีเจอร์เพิ่มเติมต่าง ๆ เช่น การรองรับ TypeScript และการทดสอบ:

<div class="language-sh"><pre><code><span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">ชื่อโปรเจ็กต์: <span style="color:#888;">… <span style="color:#89DDFF;">&lt;</span><span style="color:#888;">ชื่อโปรเจ็กต์ของคุณ</span><span style="color:#89DDFF;">&gt;</span></span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">เพิ่ม TypeScript หรือไม่? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">ไม่</span> / ใช่</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">เพิ่ม JSX Support หรือไม่? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">ไม่</span> / ใช่</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">เพิ่ม Vue Router สำหรับพัฒนา Single Page Application หรือไม่? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">ไม่</span> / ใช่</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">เพิ่ม Pinia สำหรับการจัดการสถานะหรือไม่? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">ไม่</span> / ใช่</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">เพิ่ม Vitest สำหรับการทดสอบหน่วยหรือไม่? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">ไม่</span> / ใช่</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">เพิ่มโซลูชันการทดสอบ End-to-End หรือไม่? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">ไม่</span> / Cypress / Nightwatch / Playwright</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">เพิ่ม ESLint สำหรับตรวจสอบคุณภาพของโค้ดหรือไม่? <span style="color:#888;">… ไม่ / <span style="color:#89DDFF;text-decoration:underline">ใช่</span></span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">เพิ่ม Prettier สำหรับจัดรูปแบบโค้ดหรือไม่? <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">ไม่</span> / ใช่</span></span>
<span style="color:var(--vt-c-green);">✔</span> <span style="color:#A6ACCD;">เพิ่มส่วนขยาย Vue DevTools 7 สำหรับการดีบักหรือไม่? (experimental) <span style="color:#888;">… <span style="color:#89DDFF;text-decoration:underline">ไม่</span> / ใช่</span></span>
<span></span>
<span style="color:#A6ACCD;">สร้างโปรเจ็กต์ใน ./<span style="color:#89DDFF;">&lt;</span><span style="color:#888;">ชื่อโปรเจ็กต์ของคุณ</span><span style="color:#89DDFF;">&gt;</span>...</span>
<span style="color:#A6ACCD;">เสร็จสิ้น.</span></code></pre></div>

หากคุณไม่แน่ใจเกี่ยวกับตัวเลือกใด ให้เลือก `ไม่` โดยการกด enter ในตอนนี้ เมื่อโปรเจ็กต์ถูกสร้างแล้ว ให้ทำตามคำแนะนำเพื่อติดตั้ง dependencies และเริ่ม dev server:

<VTCodeGroup>
  <VTCodeGroupTab label="npm">

```sh-vue
$ cd {{'<ชื่อโปรเจ็กต์ของคุณ>'}}
$ npm install
$ npm run dev
```

  </VTCodeGroupTab>
  <VTCodeGroupTab label="pnpm">

```sh-vue
$ cd {{'<ชื่อโปรเจ็กต์ของคุณ>'}}
$ pnpm install
$ pnpm run dev
```

  </VTCodeGroupTab>
  <VTCodeGroupTab label="yarn">

```sh-vue
$ cd {{'<ชื่อโปรเจ็กต์ของคุณ>'}}
$ yarn
$ yarn dev
```

  </VTCodeGroupTab>
  <VTCodeGroupTab label="bun">

```sh-vue
$ cd {{'<ชื่อโปรเจ็กต์ของคุณ>'}}
$ bun install
$ bun run dev
```

  </VTCodeGroupTab>
</VTCodeGroup>

ตอนนี้คุณควรจะมีโปรเจ็กต์ Vue แรกของคุณที่กำลังทำงานแล้ว! โปรดทราบว่าคอมโพเนนต์ตัวอย่างในโปรเจ็กต์ที่สร้างขึ้นจะถูกเขียนโดยใช้ [Composition API](/guide/introduction#composition-api) และ `<script setup>` แทนที่จะเป็น [Options API](/guide/introduction#options-api) นี่คือคำแนะนำเพิ่มเติม:

- การตั้งค่า IDE ที่แนะนำคือ [Visual Studio Code](https://code.visualstudio.com/) + [ส่วนขยายทางการของ Vue](https://marketplace.visualstudio.com/items?itemName=Vue.volar) หากคุณใช้ตัวแก้ไขอื่น ๆ ให้ตรวจสอบ [ส่วนการรองรับ IDE](/guide/scaling-up/tooling#ide-support).
- รายละเอียดเพิ่มเติมเกี่ยวกับเครื่องมือ รวมถึงการผสานรวมกับเฟรมเวิร์กฝั่ง backend อยู่ใน [คู่มือเครื่องมือ](guide/scaling-up/tooling).
- หากต้องการเรียนรู้เพิ่มเติมเกี่ยวกับเครื่องมือ build ที่ใช้เบื้องหลัง ให้ตรวจสอบ [Vite docs](https://vitejs.dev).
- หากคุณเลือกใช้ TypeScript ให้ดู [คู่มือการใช้งาน TypeScript](typescript/overview).

เมื่อคุณพร้อมที่จะนำแอปของคุณไปผลิต ให้รันคำสั่งต่อไปนี้:

<VTCodeGroup>
  <VTCodeGroupTab label="npm">

```sh
$ npm run build
```

  </VTCodeGroupTab>
  <VTCodeGroupTab label="pnpm">

```sh
$ pnpm run build
```

  </VTCodeGroupTab>
  <VTCodeGroupTab label="yarn">

```sh
$ yarn build
```

  </VTCodeGroupTab>
  <VTCodeGroupTab label="bun">

```sh
$ bun run build
```

  </VTCodeGroupTab>
</VTCodeGroup>

คำสั่งนี้จะสร้างแอพลิเคชั่นสำหรับการนำไปใช้งานจริง (Production) โดยจะถูกเก็บเอาไว้ในไดเรกทอรี `./dist` ของโปรเจ็กต์คุณ ตรวจสอบ [คู่มือการปรับใช้ในโปรดักชัน](/guide/best-practices/production-deployment) เพื่อเรียนรู้เพิ่มเติมเกี่ยวกับการนำแอปของคุณไปใช้งานจริง

[ขั้นตอนถัดไป >](#next-steps)

## การใช้ Vue จาก CDN {#using-vue-from-cdn}

คุณสามารถใช้ Vue ได้โดยตรงจาก CDN ผ่านแท็ก script:

```html
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
```

ในที่นี้เราใช้ [unpkg](https://unpkg.com/), แต่คุณยังสามารถใช้ CDN ใดก็ได้ที่ให้บริการแพ็กเกจ npm เช่น [jsdelivr](https://www.jsdelivr.com/package/npm/vue) หรือ [cdnjs](https://cdnjs.com/libraries/vue) แน่นอน คุณยังสามารถดาวน์โหลดไฟล์นี้และให้บริการด้วยตัวเองได้เช่นกัน

เมื่อใช้ Vue จาก CDN จะไม่มี "ขั้นตอนการ build" ที่เกี่ยวข้อง ซึ่งทำให้การตั้งค่าง่ายขึ้นมาก และเหมาะสำหรับการเพิ่มประสิทธิภาพให้กับ HTML แบบสแตติกหรือการผสานรวมกับเฟรมเวิร์กฝั่ง backend อย่างไรก็ตาม คุณจะไม่สามารถใช้ไวยากรณ์ของ Single-File Component (SFC) ได้

### การใช้ Global Build {#using-the-global-build}

ลิงก์ข้างต้นโหลด _global build_ ของ Vue ซึ่ง API ระดับบนทั้งหมดถูกแสดงเป็นพร็อพเพอร์ตี้ในออบเจ็กต์ `Vue` นี่คือตัวอย่างเต็ม ๆ ของการใช้ global build:

<div class="options-api">

```html
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>

<div id="app">{{ message }}</div>

<script>
  const { createApp } = Vue

  createApp({
    data() {
      return {
        message: 'Hello Vue!'
      }
    }
  }).mount('#app')
</script>
```

[ตัวอย่างใน CodePen >](https://codepen.io/vuejs-examples/pen/QWJwJLp)

</div>

<div class="composition-api">

```html
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>

<div id="app">{{ message }}</div>

<script>
  const { createApp, ref } = Vue

  createApp({
    setup() {
      const message = ref('Hello vue!')
      return {
        message
      }
    }
  }).mount('#app')
</script>
```

[ตัวอย่างใน Codepen >](https://codepen.io/vuejs-examples/pen/eYQpQEG)

:::tip
ตัวอย่างหลายตัวอย่างสำหรับ Composition API ในคู่มือจะใช้ไวยากรณ์ `<script setup>` ซึ่งจำเป็นต้องใช้เครื่องมือ build หากคุณต้องการใช้ Composition API โดยไม่ต้องมีขั้นตอนการ build โปรดดูการใช้งานตัวเลือก [`setup()`](/api/composition-api-setup)
:::

</div>

### การใช้ ES Module Build {#using-the-es-module-build}

ในส่วนที่เหลือของเอกสารนี้ เราจะใช้ไวยากรณ์ [ES modules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules) เป็นหลัก เบราว์เซอร์สมัยใหม่ส่วนใหญ่รองรับ ES modules โดยกำเนิดอยู่แล้ว (natively) ดังนั้นเราสามารถใช้ Vue จาก CDN ผ่าน ES modules ได้ดังนี้:

<div class="options-api">

```html{3,4}
<div id="app">{{ message }}</div>

<script type="module">
  import { createApp } from 'https://unpkg.com/vue@3/dist/vue.esm-browser.js'

  createApp({
    data() {
      return {
        message: 'Hello Vue!'
      }
    }
  }).mount('#app')
</script>
```

</div>

<div class="composition-api">

```html{3,4}
<div id="app">{{ message }}</div>

<script type="module">
  import { createApp, ref } from 'https://unpkg.com/vue@3/dist/vue.esm-browser.js'

  createApp({
    setup() {
      const message = ref('Hello Vue!')
      return {
        message
      }
    }
  }).mount('#app')
</script>
```

</div>

โปรดสังเกตว่าเราใช้ `<script type="module">` และ URL ของ CDN ที่นำเข้าจะชี้ไปที่ **ES modules build** ของ Vue

<div class="options-api">

[ตัวอย่างใน CodePen >](https://codepen.io/vuejs-examples/pen/VwVYVZO)

</div>
<div class="composition-api">

[ตัวอย่างใน CodePen >](https://codepen.io/vuejs-examples/pen/MWzazEv)

</div>

### การเปิดใช้งาน Import maps {#enabling-import-maps}

ในตัวอย่างข้างต้น เราได้นำเข้าจาก URL ของ CDN โดยตรง แต่ในส่วนที่เหลือของเอกสารนี้ คุณจะเห็นโค้ดที่มีลักษณะดังนี้:

```js
import { createApp } from 'vue'
```

เราสามารถสอนเบราว์เซอร์ให้รู้ว่าจะค้นหาการนำเข้า `vue` ได้ที่ไหนโดยใช้ [Import Maps](https://caniuse.com/import-maps):

<div class="options-api">

```html{1-7,12}
<script type="importmap">
  {
    "imports": {
      "vue": "https://unpkg.com/vue@3/dist/vue.esm-browser.js"
    }
  }
</script>

<div id="app">{{ message }}</div>

<script type="module">
  import { createApp } from 'vue'

  createApp({
    data() {
      return {
        message: 'Hello Vue!'
      }
    }
  }).mount('#app')
</script>
```

[ตัวอย่างใน CodePen >](https://codepen.io/vuejs-examples/pen/wvQKQyM)

</div>

<div class="composition-api">

```html{1-7,12}
<script type="importmap">
  {
    "imports": {
      "vue": "https://unpkg.com/vue@3/dist/vue.esm-browser.js"
    }
  }
</script>

<div id="app">{{ message }}</div>

<script type="module">
  import { createApp, ref } from 'vue'

  createApp({
    setup() {
      const message = ref('Hello Vue!')
      return {
        message
      }
    }
  }).mount('#app')
</script>
```

[ตัวอย่างใน CodePen >](https://codepen.io/vuejs-examples/pen/YzRyRYM)

</div>

คุณสามารถเพิ่มรายการสำหรับ dependencies อื่น ๆ ลงใน import map ได้เช่นกัน แต่ต้องแน่ใจว่ามันชี้ไปที่เวอร์ชันของ ES modules ของไลบรารีที่คุณต้องการใช้

:::tip การรองรับเบราว์เซอร์ของ Import Maps
Import Maps เป็นฟีเจอร์ที่ค่อนข้างใหม่ของเบราว์เซอร์ อย่าลืมใช้เบราว์เซอร์ที่อยู่ในช่วง [การรองรับ](https://caniuse.com/import-maps) โดยเฉพาะอย่างยิ่ง รองรับเฉพาะใน Safari 16.4+
:::

:::warning หมายเหตุเกี่ยวกับการใช้งานในโปรดักชัน
ตัวอย่างที่เราใช้มาจนถึงตอนนี้ใช้ development build ของ Vue - หากคุณตั้งใจจะใช้ Vue จาก CDN ในโปรดักชัน ตรวจสอบ [คู่มือการปรับใช้ในโปรดักชัน](/guide/best-practices/production-deployment#without-build-tools)

ถึงแม้ว่าจะสามารถใช้ Vue ได้โดยไม่ต้องใช้ build system วิธีการทางเลือกที่ควรพิจารณาคือการใช้ [`vuejs/petite-vue`](https://github.com/vuejs/petite-vue) ซึ่งอาจเหมาะกับบริบทที่เคยใช้ [`jquery/jquery`](https://github.com/jquery/jquery) (ในอดีต) หรือ [`alpinejs/alpine`](https://github.com/alpinejs/alpine) (ในปัจจุบัน) แทน
:::

### การแยกโมดูล {#splitting-up-the-modules}

เมื่อเราลงลึกในคู่มือ เราอาจจำเป็นต้องแยกโค้ดออกเป็นไฟล์ JavaScript แยกต่างหาก เพื่อให้จัดการได้ง่ายขึ้น ตัวอย่างเช่น:

```html
<!-- index.html -->
<div id="app"></div>

<script type="module">
  import { createApp } from 'vue'
  import MyComponent from './my-component.js'

  createApp(MyComponent).mount('#app')
</script>
```

<div class="options-api">

```js
// my-component.js
export default {
  data() {
    return { count: 0 }
  },
  template: `<div>Count is: {{ count }}</div>`
}
```

</div>
<div class="composition-api">

```js
// my-component.js
import { ref } from 'vue'
export default {
  setup() {
    const count = ref(0)
    return { count }
  },
  template: `<div>Count is: {{ count }}</div>`
}
```

</div>

หากคุณเปิด `index.html` ข้างต้นในเบราว์เซอร์โดยตรง คุณจะพบว่ามันเกิดข้อผิดพลาด เนื่องจาก ES modules ไม่สามารถทำงานผ่านโปรโตคอล `file://` ซึ่งเป็นโปรโตคอลที่เบราว์เซอร์ใช้เมื่อคุณเปิดไฟล์แบบ Local file

เนื่องด้วยเหตุผลด้านความปลอดภัย ES modules สามารถทำงานได้ผ่านโปรโตคอล `http://` เท่านั้น ซึ่งเป็นโปรโตคอลที่เบราว์เซอร์ใช้เมื่อเปิดหน้าเว็บ ในการทำให้ ES modules ทำงานบนเครื่องของเรา เราจำเป็นต้องให้บริการ `index.html` ผ่านโปรโตคอล `http://` โดยใช้ local HTTP server.

ในการเริ่มเซิร์ฟเวอร์แบบ local HTTP server ให้ตรวจสอบว่าคุณได้ติดตั้ง [Node.js](https://nodejs.org/en/) แล้ว จากนั้นรันคำสั่ง `npx serve` จาก command line ในไดเรกทอรีเดียวกับไฟล์ HTML ของคุณ คุณยังสามารถใช้เซิร์ฟเวอร์ HTTP อื่น ๆ ที่สามารถให้บริการไฟล์สแตติกพร้อมประเภท MIME ที่ถูกต้องได้เช่นกัน

คุณอาจสังเกตเห็นว่าตัวอย่างเทมเพลตของคอมโพเนนต์ถูก inlined เป็นสตริง JavaScript หากคุณใช้ VS Code คุณสามารถติดตั้ง [es6-string-html](https://marketplace.visualstudio.com/items?itemName=Tobermory.es6-string-html) เพื่อให้ไฮไลต์ไวยากรณ์สำหรับสตริงเหล่านี้โดยการเพิ่มคำสั่ง `/*html*/` ที่หน้าสตริง

## ขั้นตอนถัดไป {#next-steps}

หากคุณข้าม [บทนำ](/guide/introduction) ไป เราขอแนะนำให้อ่านก่อนที่จะดำเนินการต่อไปยังส่วนที่เหลือของเอกสาร

<div class="vt-box-container next-steps">
  <a class="vt-box" href="/guide/essentials/application.html">
    <p class="next-steps-link">ดำเนินการต่อตามคู่มือ</p>
    <p class="next-steps-caption">คู่มือนี้จะนำคุณผ่านทุกแง่มุมของเฟรมเวิร์กอย่างละเอียด</p>
  </a>
  <a class="vt-box" href="/tutorial/">
    <p class="next-steps-link">ลองทำตามบทเรียน</p>
    <p class="next-steps-caption">สำหรับผู้ที่ชอบเรียนรู้ผ่านการปฏิบัติ</p>
  </a>
  <a class="vt-box" href="/examples/">
    <p class="next-steps-link">ดูตัวอย่าง</p>
    <p class="next-steps-caption">สำรวจตัวอย่างคุณสมบัติหลักและงาน UI ทั่วไป</p>
  </a>
</div>
