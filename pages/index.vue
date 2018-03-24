<template>
  <main>
    <ul>
      <li v-for="card in cards" :key="card.id" :class="card.class">{{ card.text }}-{{ card.id }}</li>
    </ul>
  </main>
</template>

<script>
export default {
  data: () => {
    return {
      cards: [
        { id: 1, text: 'text', class: 'card01' },
        { id: 2, text: 'text', class: 'card02' },
        { id: 3, text: 'text', class: 'card03' },
        { id: 4, text: 'text', class: 'card04' },
        { id: 5, text: 'text', class: 'card05' },
        { id: 6, text: 'text', class: 'card06' },
        { id: 7, text: 'text', class: 'card07' },
        { id: 8, text: 'text', class: 'card08' }
      ],
      orders: {
        card01: 'card02',
        card02: 'card03',
        card03: 'card05',
        card05: 'card08',
        card04: 'card01',
        card06: 'card04',
        card07: 'card06',
        card08: 'card07'
      }
    }
  },
  created() {
    setInterval(() => {
      this.changeClass()
    }, 5000)
  },
  methods: {
    changeClass() {
      _.each(this.cards, card => {
        card.class = this.orders[card.class]
      })
    }
  }
}
</script>

<style lang='scss' scoped>
main {
  width: 400px;
  height: 400px;
  margin: 10px auto 0 auto;
}

ul {
  width: 100%;
  height: 100%;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 1fr 1fr 1fr;
  grid-gap: 10px;
  grid-template-areas:
    'card01 card02 card03'
    'card04  skip  card05'
    'card06 card07 card08';

  li {
    list-style: none;
    background-color: #eee;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .card01 {
    grid-column: 1 / 2;
    grid-row: 1 / 2;
    grid-area: card01;
  }
  .card02 {
    grid-column: 2 / 3;
    grid-row: 1 / 2;
    grid-area: card02;
  }
  .card03 {
    grid-column: 3 / 4;
    grid-row: 1 / 2;
    grid-area: card03;
  }
  .card04 {
    grid-column: 1 / 2;
    grid-row: 2 / 3;
    grid-area: card04;
  }
  .card05 {
    grid-column: 3 / 4;
    grid-row: 2 / 3;
    grid-area: card05;
  }
  .card06 {
    grid-column: 1 / 2;
    grid-row: 3 / 4;
    grid-area: card06;
  }
  .card07 {
    grid-column: 2 / 3;
    grid-row: 3 / 4;
    grid-area: card07;
  }
  .card08 {
    grid-column: 3 / 4;
    grid-row: 3 / 4;
    grid-area: card08;
  }
}
</style>
