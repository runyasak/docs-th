# สร้างแอพพลิเคชั่นด้วย Vue {#creating-a-vue-application}

## ตัวแทนของแอปพลิเคชัน (The application instance) {#the-application-instance}

ทุกแอปพลิเคชันของ Vue จะเริ่มต้นด้วยการสร้าง **ตัวแทนของแอปพลิเคชัน** ใหม่ด้วยฟังก์ชัน [`createApp`](/api/application#createapp):

```js
import { createApp } from 'vue'

const app = createApp({
  /* ตัวเลือกของ root component */
})
```

## คอมโพแนนซ์หลัก (Root Component) {#the-root-component}

อ็อบเจกต์ที่เราส่งไปใน `createApp` จริงๆ แล้วคือ component หนึ่ง ทุกแอปจะต้องมี "root component" ที่สามารถมี component อื่นๆ เป็นลูกได้

ถ้าคุณใช้ Single-File Components เรามักจะ import root component มาจากไฟล์อื่น:

```js
import { createApp } from 'vue'
// import root component App จาก single-file component
import App from './App.vue'

const app = createApp(App)
```

แม้ว่าในตัวอย่างหลายๆ อันในไกด์นี้จะต้องการแค่ component เดียว แต่แอปพลิเคชันจริงๆ ส่วนมากจะถูกจัดเรียงเป็น tree ของ component ที่ซ้อนกันและสามารถใช้งานซ้ำได้ ตัวอย่างเช่น tree ของ component ในแอป To-do อาจจะดูเป็นแบบนี้:

```
App (root component)
├─ TodoList
│  └─ TodoItem
│     ├─ TodoDeleteButton
│     └─ TodoEditButton
└─ TodoFooter
   ├─ TodoClearButton
   └─ TodoStatistics
```

ในส่วนถัดๆ ไปของไกด์ เราจะพูดถึงวิธีการนิยามและรวมหลายๆ component เข้าด้วยกัน แต่ก่อนหน้านั้น เราจะมุ่งเน้นไปที่สิ่งที่เกิดขึ้นภายใน component เดียว (Single Component)

## การเชื่อมต่อแอปกับหน้าเว็บ (mounting the app) {#mounting-the-app}

ตัวแทนของแอปพลิเคชัน (Instance) จะไม่แสดงผลอะไรจนกว่าจะมีการเรียกใช้เมธอด `.mount()` มันต้องการอาร์กิวเมนต์ "container" ซึ่งสามารถเป็น element จริงๆ ใน DOM หรือ selector string ก็ได้:

```html
<div id="app"></div>
```

```js
app.mount('#app')
```

เนื้อหาของ root component ของแอปจะถูกแสดงผลภายใน container element โดย container element เองจะไม่ถือว่าเป็นส่วนหนึ่งของแอป

เมธอด `.mount()` ควรถูกเรียกหลังจากการตั้งค่าและการลงทะเบียน asset ของแอปทั้งหมดเรียบร้อยแล้ว นอกจากนี้ยังควรสังเกตว่าค่าที่ถูกส่งกลับจาก `.mount()` ซึ่งแตกต่างจากเมธอดการลงทะเบียน asset อื่นๆ ค่าที่ส่งกลับคือตัวแทนของ root component แทนที่จะเป็นตัวแทนของแอปพลิเคชัน

### In-DOM Root Component Template {#in-dom-root-component-template}

โดยปกติแล้ว template สำหรับ root component จะเป็นส่วนหนึ่งของตัว component เอง แต่ก็สามารถแยก template ออกมาได้โดยเขียนไว้ภายใน mount container:

```html
<div id="app">
  <button @click="count++">{{ count }}</button>
</div>
```

```js
import { createApp } from 'vue'

const app = createApp({
  data() {
    return {
      count: 0
    }
  }
})

app.mount('#app')
```

Vue จะใช้ `innerHTML` ของ container เป็น template โดยอัตโนมัติ ถ้า root component ไม่มีตัวเลือก `template` อยู่แล้ว

In-DOM templates มักจะถูกใช้ในแอปที่ [ใช้ Vue โดยไม่มีขั้นตอนการ build](/guide/quick-start.html#using-vue-from-cdn) และยังสามารถใช้ร่วมกับเฟรมเวิร์กที่ทำงานฝั่งเซิร์ฟเวอร์ ซึ่ง template ของ root อาจจะถูกสร้างแบบไดนามิกโดยเซิร์ฟเวอร์

## การตั้งค่าแอป {#app-configurations}

ตัวแทนของแอปพลิเคชันจะมีอ็อบเจกต์ `.config` ที่เปิดโอกาสให้เราตั้งค่าบางอย่างในระดับแอปได้ ตัวอย่างเช่น การกำหนด error handler ที่จัดการกับข้อผิดพลาดจากทุก component ลูก:

```js
app.config.errorHandler = (err) => {
  /* handle error */
}
```

ตัวแทนของแอปพลิเคชันยังมีเมธอดบางอย่างที่ช่วยในการลงทะเบียน asset ในระดับแอป ตัวอย่างเช่น การลงทะเบียน component:

```js
app.component('TodoDeleteButton', TodoDeleteButton)
```

สิ่งนี้ทำให้ `TodoDeleteButton` สามารถถูกใช้งานได้ทุกที่ในแอป เราจะพูดถึงการลงทะเบียน component และประเภทของ asset อื่นๆ ในส่วนถัดๆ ไปของไกด์ คุณสามารถดูรายการ API ของตัวแทนของแอปพลิเคชันได้ใน [API reference](/api/application)

อย่าลืมตั้งค่าทั้งหมดก่อนที่จะ mount แอป!

## ตัวแทนของแอปพลิเคชันหลายตัว {#multiple-application-instances}

คุณไม่ได้ถูกจำกัดให้มีแค่ตัวแทนของแอปพลิเคชันเพียงตัวเดียวในหน้าเดียว API `createApp` อนุญาตให้หลายแอปพลิเคชัน Vue อยู่ร่วมกันในหน้าเดียว แต่ละแอปจะมี scope ของการตั้งค่าและ asset แบบ global เป็นของตัวเอง:

```js
const app1 = createApp({
  /* ... */
})
app1.mount('#container-1')

const app2 = createApp({
  /* ... */
})
app2.mount('#container-2')
```

ถ้าคุณใช้ Vue เพื่อเพิ่มความสามารถให้กับ HTML ที่เรนเดอร์จากฝั่งเซิร์ฟเวอร์ และคุณต้องการให้ Vue ควบคุมแค่บางส่วนของหน้าที่มีขนาดใหญ่ อย่าทำการ mount ตัวแทนของแอป Vue เพียงตัวเดียวครอบคลุมทั้งหน้า ควรสร้างตัวแทนแอปเล็กๆ หลายตัว และทำการ mount พวกมันบน element ที่พวกมันรับผิดชอบ
