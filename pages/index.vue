<template>
  <main>
    <transition-group name="card-block" tag="ul">
      <li v-for="card in cards" :key="card.id" :class="card.class" :style="{ background: card.color }">{{ card.text }}</li>
    </transition-group>
  </main>
</template>

<script>
export default {
  data: () => {
    return {
      cards: [
        { id: 0, class: '', color: '', text: '周りが回る' },
        { id: 1, class: 'card01', color: '#e8aeb7', text: 'text-01' },
        { id: 2, class: 'card02', color: '#b8e1ff', text: 'text-02' },
        { id: 3, class: 'card03', color: '#a9fff7', text: 'text-03' },
        { id: 4, class: 'card04', color: '#94fbab', text: 'text-04' },
        { id: 5, class: 'card05', color: '#82aba1', text: 'text-05' },
        { id: 6, class: 'card06', color: '#f9a03f', text: 'text-06' },
        { id: 7, class: 'card07', color: '#f7d488', text: 'text-07' },
        { id: 8, class: 'card08', color: '#eaefb1', text: 'text-08' }
      ],
      MIN: 1,
      MAX: 8
    }
  },
  created() {
    setInterval(() => {
      _.each(this.cards, card => {
        let id = Number(card.class.slice(-2))
        if (this.MAX <= id) {
          card.class = 'card01'
        } else if (this.MIN <= id && id < this.MAX) {
          card.class = 'card' + ('00' + ++id).slice(-2)
        }
      })
    }, 2000)
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
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
  grid-gap: 10px;
  grid-template-areas:
    'card01 card02 card03'
    'card08 ...... card04'
    'card07 card06 card05';

  li {
    list-style: none;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .card-block-move {
    transition: transform 1s;
  }

  .card01 {
    grid-area: card01;
  }
  .card02 {
    grid-area: card02;
  }
  .card03 {
    grid-area: card03;
  }
  .card04 {
    grid-area: card04;
  }
  .card05 {
    grid-area: card05;
  }
  .card06 {
    grid-area: card06;
  }
  .card07 {
    grid-area: card07;
  }
  .card08 {
    grid-area: card08;
  }
}
</style>
