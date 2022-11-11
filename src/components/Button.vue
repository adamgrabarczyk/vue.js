<script>
export default {
  data() {
    return {
      count: 0,
      myColor: {
        color: '#fab'
      },
      coments: [
        {
            name: 'Adam',
            coment: 'ad,andankanslkbksamfsdlkn'
        },
        {
            name: 'Julia',
            coment: 'asd  as fsdlkn'
        },
        {
            name: 'Basia',
            coment: 'adasda   asd asd asd asd asd asdafad asdad n'
        }
      ]
    }
  },
  methods: {
    increment() {
      this.count++
    },
    decrement() {
      this.count--
    }
  }
}
</script>

<template>
  <button @click="increment">+</button>
  <p :style="myColor">count is: {{ count }}</p>
  <button @click="decrement">-</button>
  <label for="color" >input change color</label>
  <input name="color" v-model="myColor.color"/>
  <p v-for="content in coments">{{content.name}}</p>
</template>