---
footer: false
---

# {#introduction}

:::info คุณกำลังอ่านเอกสารของ vue 3!

- Vue 2 เลิกซัพพอร์ตเเละพัฒนาเมื่อวันที่ **31 ธันวาคม 2023**. สามารถอ่านเเละเรียนรู้เพิ่มเติมได้ที่ [Vue 2 EOL](https://v2.vuejs.org/eol/).
- อัพเกรดจาก Vue 2? สามารถอ่านเพิ่มเติมได้ที่ [คู่มือการอัพเกรด](https://v3-migration.vuejs.org/).
  :::

<style src="@theme/styles/vue-mastery.css"></style>
<div class="vue-mastery-link">
  <a href="https://www.vuemastery.com/courses/" target="_blank">
    <div class="banner-wrapper">
      <img class="banner" alt="Vue Mastery banner" width="96px" height="56px" src="https://storage.googleapis.com/vue-mastery.appspot.com/flamelink/media/vuemastery-graphical-link-96x56.png" />
    </div>
    <p class="description">เรียนรู้ตัวอย่างของ Vue ผ่านวีดีโอได้บน <span>VueMastery.com</span></p>
    <div class="logo-wrapper">
        <img alt="Vue Mastery Logo" width="25px" src="https://storage.googleapis.com/vue-mastery.appspot.com/flamelink/media/vue-mastery-logo.png" />
    </div>
  </a>
</div>

## Vue คืออะไร? {#what-is-vue}

Vue (ออกเสียงว่า วิว) เป็น JavaScript framework สำหรับสร้างหน้าเว็บไซต์เพื่อติดต่อกับผู้ใช้งาน(user interfaces). โดยสร้างมาจากพื้นฐานภาษาของ HTML, CSS เเละ JavaScript พร้อมทั้งรองรับการเขียนในรูปแบบของ component-based ซึ่งจะช่วยให้คุณสามารถพัฒนาเว็บไซต์สำหรับติดต่อกับผู้ใช้งานได้อย่างมีประสิทธิภาพ ไม่ว่าจะเขียนซับซ้อนมากขนาดไหนก็ตาม

นี่เป็นตัวอย่างฉบับย่อ:

<div class="options-api">

```js
import { createApp } from 'vue'

createApp({
  data() {
    return {
      count: 0
    }
  }
}).mount('#app')
```

</div>
<div class="composition-api">

```js
import { createApp, ref } from 'vue'

createApp({
  setup() {
    return {
      count: ref(0)
    }
  }
}).mount('#app')
```

</div>

```vue-html
<div id="app">
  <button @click="count++">
    จำนวนการกด : {{ count }}
  </button>
</div>
```

**ผลลัพธ์**

<script setup>
import { ref } from 'vue'
const count = ref(0)
</script>

<div class="demo">
  <button @click="count++">
    จำนวนการกด : {{ count }}
  </button>
</div>

จากตัวอย่างด้านบนจะเเสดง 2 คุณสมบัติของ vue:

- **การประมวลผลเชิงบรรยาย (Declarative Rendering)**: Vue ได้เพิ่มความสามารถพื้นฐานของ HTML ด้วยวิธีการใช้ไวยากรณ์เทมเพลต (Template syntax) ที่ทำให้เราสามารถอธิบายผลลัพธ์ของ HTML ตามค่าสถานะ (State) ของ JavaScript.

- **การทำงานแบบตอบสนอง (Reactivity)**: Vue จะติดตามการเปลี่ยนแปลงค่าสถานะของ JavaScript โดยอัตโนมัติ เเละอัปเดต DOM อย่างมีประสิทธิภาพเมื่อเกิดการเปลี่ยนแปลง.

คุณอาจจะมีคำถามอยู่แล้ว - ไม่ต้องกังวล เราจะครอบคลุมทุกเรื่องในเอกสารนี้ ในตอนนี้โปรดอ่านต่อเพื่อให้คุณมีความเข้าใจภาพรวมของสิ่งที่ Vue นำเสนอ

:::tip ข้อกำหนดเบื้องต้น
เนื้อหาที่เหลือของเอกสารนี้ถือว่าคุณมีความคุ้นเคยเบื้องต้นกับ HTML, CSS และ JavaScript หากคุณเป็นมือใหม่สำหรับการพัฒนาเว็บ frontend อาจจะไม่ใช่ไอเดียที่ดีที่จะเริ่มต้นด้วยเฟรมเวิร์กในทันที ควรเข้าใจพื้นฐานก่อนแล้วค่อยกลับมา คุณสามารถตรวจสอบระดับความรู้ของคุณได้จากบทสรุปเหล่านี้: [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript), [HTML](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML), และ [CSS](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps) ประสบการณ์ก่อนหน้ากับเฟรมเวิร์กอื่นอาจช่วยได้ แต่ไม่จำเป็น
:::

## Framework แห่งยุคสมัย (เฟรมเวิร์กที่พัฒนาตามคุณ) {#the-progressive-framework}

Vue เป็นเฟรมเวิร์กและระบบนิเวศ (ecosystem) ที่ครอบคลุมฟีเจอร์หลักที่จำเป็นในการพัฒนาเว็บ frontend แต่เนื่องจากโลกของเว็บนั้นมีความหลากหลายมาก สิ่งที่เราสร้างบนเว็บอาจแตกต่างกันอย่างมากในรูปแบบและขนาด ด้วยเหตุนี้ Vue จึงถูกออกแบบมาให้ยืดหยุ่นและสามารถนำไปใช้ได้ทีละนิดตามความต้องการของคุณ:

- เพิ่มประสิทธิภาพให้กับ HTML แบบ static โดยไม่ต้องใช้ขั้นตอน build
- ฝังเป็น Web Components บนหน้าใดก็ได้
- สร้างแอปแบบหน้าเดียว (Single-Page Application - SPA)
- รองรับ Fullstack / การเรนเดอร์ฝั่งเซิร์ฟเวอร์ (Server-Side Rendering - SSR)
- Jamstack / การสร้างเว็บไซต์แบบ static (Static Site Generation - SSG)
- รองรับการทำงานบนเดสก์ท็อป, มือถือ, WebGL และแม้กระทั่งการทำงานบน terminal

ถ้าคุณรู้สึกว่าแนวคิดเหล่านี้ยากไม่ต้องกังวล! บทเรียนและคู่มือจำเป็นต้องใช้เพียงความรู้พื้นฐานของ HTML และ JavaScript และคุณควรจะตามเนื้อหาได้แม้จะยังไม่เป็นผู้เชี่ยวชาญในเรื่องเหล่านี้

หากคุณเป็นนักพัฒนาที่มีประสบการณ์และสนใจวิธีการผสาน Vue เข้ากับ stack ของคุณ หรืออยากรู้ว่าคำเหล่านี้หมายถึงอะไร เราจะอธิบายรายละเอียดเพิ่มเติมในหัวข้อ [Ways of Using Vue (วิธีการใช้งาน Vue)](/guide/extras/ways-of-using-vue)

ถึงแม้ว่า Vue จะยืดหยุ่น แต่ความรู้พื้นฐานเกี่ยวกับการทำงานของ Vue นั้นใช้ได้กับทุกกรณีการใช้งาน แม้ว่าตอนนี้คุณจะเป็นเพียงผู้เริ่มต้น ความรู้ที่ได้มาจะยังมีประโยชน์เมื่อคุณเติบโตและรับมือกับโปรเจ็กต์ที่ซับซ้อนมากขึ้นในอนาคต หากคุณเป็นผู้เชี่ยวชาญแล้ว คุณสามารถเลือกวิธีที่เหมาะสมที่สุดในการใช้ประโยชน์จาก Vue ตามปัญหาที่คุณกำลังแก้ไข ในขณะที่ยังคงรักษาประสิทธิภาพในการทำงาน นี่คือเหตุผลที่เราเรียก Vue ว่า "เฟรมเวิร์กที่พัฒนาตามคุณ": มันเป็นเฟรมเวิร์กที่สามารถเติบโตไปพร้อมกับคุณและปรับตัวตามความต้องการของคุณ

## คอมโพเเนนซ์แบบไฟล์เดียว (Single-File Components) {#single-file-components}

ในโปรเจ็กต์ Vue ที่ใช้เครื่องมือ build เราจะเขียนคอมโพเนนต์ของ Vue โดยใช้รูปแบบไฟล์ที่คล้ายกับ HTML ที่เรียกว่า **Single-File Component** (หรือไฟล์ที่มีนามสกุล `*.vue` เรียกย่อว่า **SFC**) ซึ่ง SFC ของ Vue ตามชื่อคือการรวบรวมตรรกะของคอมโพเนนต์ (JavaScript), เทมเพลต (HTML), และสไตล์ (CSS) ไว้ในไฟล์เดียว นี่คือตัวอย่างก่อนหน้านี้ที่เขียนในรูปแบบ SFC:

<div class="options-api">

```vue
<script>
export default {
  data() {
    return {
      count: 0
    }
  }
}
</script>

<template>
  <button @click="count++">Count is: {{ count }}</button>
</template>

<style scoped>
button {
  font-weight: bold;
}
</style>
```

</div>
<div class="composition-api">

```vue
<script setup>
import { ref } from 'vue'
const count = ref(0)
</script>

<template>
  <button @click="count++">Count is: {{ count }}</button>
</template>

<style scoped>
button {
  font-weight: bold;
}
</style>
```

</div>

SFC เป็นฟีเจอร์หลักของ Vue และเป็นวิธีแนะนำในการเขียนคอมโพเนนต์ของ Vue **หาก** กรณีการใช้งานของคุณจำเป็นต้องใช้เครื่องมือ build คุณสามารถเรียนรู้เพิ่มเติมเกี่ยวกับ [วิธีและเหตุผลของการใช้ SFC](/guide/scaling-up/sfc) ในหัวข้อเฉพาะ - แต่ตอนนี้เพียงแค่รู้ว่า Vue จะจัดการเครื่องมือ build ให้คุณเอง

## สไตล์การเขียน {#api-styles}

คอมโพเนนต์ของ Vue สามารถเขียนได้ใน 2 สไตล์ API ที่แตกต่างกัน: **Options API** และ **Composition API**

### Options API {#options-api}

ใน Options API เราจะกำหนดตรรกะ (logic) ของคอมโพเนนต์โดยใช้ object ของ options เช่น `data`, `methods`, และ `mounted` คุณสมบัติที่กำหนดโดย options จะถูกเปิดเผยบน `this` ภายในฟังก์ชัน ซึ่งชี้ไปยังอินสแตนซ์ของคอมโพเนนต์:

```vue
<script>
export default {
  // Properties ที่ return จาก data() จะกลายเป็น state ที่สามารถตอบสนอง (reactive)
  // และจะสามารถเข้าถึงได้บน `this`.
  data() {
    return {
      count: 0
    }
  },

  // Methods เป็นฟังก์ชันที่ใช้เปลี่ยนแปลง state และทำให้เกิดการอัปเดตหน้าจอ
  // สามารถถูกผูกให้เป็น event handler ใน template ได้
  methods: {
    increment() {
      this.count++
    }
  },

  // Lifecycle hooks จะถูกเรียกในแต่ละช่วงของ lifecycle ของ component
  // ฟังก์ชันนี้จะถูกเรียกเมื่อตัว component ถูก mount (ตอนที่ component ถูกแทรกเข้าไปใน DOM)
  mounted() {
    console.log(`จำนวนเริ่มต้นคือ ${this.count}.`)
  }
}
</script>

<template>
  <button @click="increment">จำนวน คือ: {{ count }}</button>
</template>
```

[ลองใช้ใน Playground](https://play.vuejs.org/#eNptkMFqxCAQhl9lkB522ZL0HNKlpa/Qo4e1ZpLIGhUdl5bgu9es2eSyIMio833zO7NP56pbRNawNkivHJ25wV9nPUGHvYiaYOYGoK7Bo5CkbgiBBOFy2AkSh2N5APmeojePCkDaaKiBt1KnZUuv3Ky0PppMsyYAjYJgigu0oEGYDsirYUAP0WULhqVrQhptF5qHQhnpcUJD+wyQaSpUd/Xp9NysVY/yT2qE0dprIS/vsds5Mg9mNVbaDofL94jZpUgJXUKBCvAy76ZUXY53CTd5tfX2k7kgnJzOCXIF0P5EImvgQ2olr++cbRE4O3+t6JxvXj0ptXVpye1tvbFY+ge/NJZt)

### Composition API {#composition-api}

ใน Composition API เราจะกำหนดตรรกะของคอมโพเนนต์โดยใช้ฟังก์ชัน API ที่นำเข้า ใน SFCs Composition API มักจะใช้กับ [`<script setup>`](/api/sfc-script-setup) คำสั่ง `setup` เป็นตัวชี้ให้ Vue ทำการแปลงแบบ compile-time ที่ช่วยให้เราสามารถใช้ Composition API ได้ด้วยโค้ดที่เรียบง่ายขึ้น ตัวอย่างเช่น imports และตัวแปร/ฟังก์ชันที่ประกาศใน `<script setup>` สามารถนำไปใช้ในเทมเพลตได้โดยตรง

นี่คือตัวอย่างเดียวกัน แต่เขียนโดยใช้ Composition API และ `<script setup>`:

```vue
<script setup>
import { ref, onMounted } from 'vue'

// สถานะ reactive
const count = ref(0)

// ฟังก์ชันที่เปลี่ยนแปลงสถานะและทำให้เกิดการอัปเดต
function increment() {
  count.value++
}

// lifecycle hooks
onMounted(() => {
  console.log(`ค่าเริ่มต้นคือ ${count.value}.`)
})
</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>
```

[ลองใช้ใน Playground](https://play.vuejs.org/#eNpNkMFqwzAQRH9lMYU4pNg9Bye09NxbjzrEVda2iLwS0spQjP69a+yYHnRYad7MaOfiw/tqSliciybqYDxDRE7+qsiM3gWGGQJ2r+DoyyVivEOGLrgRDkIdFCmqa1G0ms2EELllVKQdRQa9AHBZ+PLtuEm7RCKVd+ChZRjTQqwctHQHDqbvMUDyd7mKip4AGNIBRyQujzArgtW/mlqb8HRSlLcEazrUv9oiDM49xGGvXgp5uT5his5iZV1f3r4HFHvDprVbaxPhZf4XkKub/CDLaep1T7IhGRhHb6WoTADNT2KWpu/aGv24qGKvrIrr5+Z7hnneQnJu6hURvKl3ryL/ARrVkuI=)

### เลือกใช้ API แบบไหนดี? {#which-to-choose}

ทั้งสอง API styles รองรับการใช้งานหลักได้เหมือนกัน พวกมันเป็นอินเทอร์เฟซที่แตกต่างกัน แต่ขับเคลื่อนด้วยระบบเดียวกัน ในความเป็นจริง Options API ถูกสร้างขึ้นบนพื้นฐานของ Composition API! แนวคิดพื้นฐานและความรู้เกี่ยวกับการทำงานของ Vue ถูกแชร์ระหว่างสองสไตล์นี้

Options API มุ่งเน้นไปที่แนวคิดของ "component instance" (`this` ที่เห็นในตัวอย่าง) ซึ่งเหมาะกับผู้ใช้ที่คุ้นเคยกับการเขียนโปรแกรมเชิงวัตถุ (OOP) มากกว่า นอกจากนี้ยังเหมาะสำหรับผู้เริ่มต้นเพราะมันซ่อนรายละเอียดการทำงานของระบบ reactive ไว้และจัดโครงสร้างโค้ดผ่านกลุ่มตัวเลือกต่าง ๆ

Composition API มุ่งเน้นการประกาศสถานะ reactive โดยตรงในฟังก์ชันและรวมสถานะจากหลายฟังก์ชันเพื่อจัดการกับความซับซ้อน มันมีความยืดหยุ่นมากกว่า แต่ก็ต้องการความเข้าใจเกี่ยวกับการทำงานของระบบ reactive ใน Vue เพื่อใช้งานอย่างมีประสิทธิภาพ อย่างไรก็ตาม ความยืดหยุ่นนี้ช่วยให้เราสร้างรูปแบบการจัดการโค้ดที่ทรงพลังยิ่งขึ้นสำหรับการจัดการและนำกลับมาใช้ใหม่

คุณสามารถเรียนรู้เพิ่มเติมเกี่ยวกับการเปรียบเทียบทั้งสองสไตล์ และข้อดีของ Composition API ใน [FAQ ของ Composition API](/guide/extras/composition-api-faq)

หากคุณเป็นมือใหม่กับ Vue นี่คือคำแนะนำทั่วไป:

- สำหรับการเรียนรู้ ให้เลือกใช้สไตล์ที่คุณรู้สึกว่าเข้าใจได้ง่ายกว่า อีกครั้งที่แนวคิดหลักส่วนใหญ่ถูกแชร์ระหว่างสองสไตล์ คุณสามารถเรียนรู้สไตล์อีกแบบได้ภายหลัง

- สำหรับการใช้งานจริง:

  - เลือกใช้ Options API หากคุณไม่ได้ใช้เครื่องมือ build หรือวางแผนจะใช้ Vue ในสถานการณ์ที่ไม่ซับซ้อน เช่น progressive enhancement

  - เลือกใช้ Composition API + Single-File Components หากคุณวางแผนจะสร้างแอปพลิเคชันเต็มรูปแบบด้วย Vue

คุณไม่จำเป็นต้องยึดติดกับสไตล์ใดสไตล์หนึ่งในช่วงการเรียนรู้ เอกสารที่เหลือจะมีตัวอย่างโค้ดในทั้งสองสไตล์ และคุณสามารถสลับระหว่างพวกมันได้ตลอดเวลาผ่าน **API Preference switches** ที่ด้านบนของแถบด้านข้างซ้าย

## ยังมีคำถามอีกไหม? {#still-got-questions}

ตรวจสอบ [FAQ](/about/faq) ของเรา

## เลือกเส้นทางการเรียนรู้ของคุณ {#pick-your-learning-path}

นักพัฒนาแต่ละคนมีรูปแบบการเรียนรู้ที่แตกต่างกัน คุณสามารถเลือกเส้นทางการเรียนรู้ที่เหมาะกับคุณได้อย่างอิสระ - แต่เราขอแนะนำให้คุณอ่านเนื้อหาทั้งหมด หากเป็นไปได้!

<div class="vt-box-container next-steps">
  <a class="vt-box" href="/tutorial/">
    <p class="next-steps-link">ลองทำตามบทเรียน</p>
    <p class="next-steps-caption">สำหรับผู้ที่ชอบเรียนรู้ผ่านการปฏิบัติ</p>
  </a>
  <a class="vt-box" href="/guide/quick-start.html">
    <p class="next-steps-link">อ่านคู่มือ</p>
    <p class="next-steps-caption">คู่มือนี้จะนำคุณผ่านทุกแง่มุมของเฟรมเวิร์กอย่างละเอียด</p>
  </a>
  <a class="vt-box" href="/examples/">
    <p class="next-steps-link">ดูตัวอย่าง</p>
    <p class="next-steps-caption">สำรวจตัวอย่างคุณสมบัติหลักและงาน UI ทั่วไป</p>
  </a>
</div>
