<template>
<div>
  <button @click="startCard">开始</button>
  <button @click="dealCard">发牌</button>
  <ul class="oringeCard">
    <li v-for="(card, index) in cards" @click="cutCard(index)" v-bind:class="[card.id, {open: card.open}]" :key='index' v-bind:title='card.title'>{{card.name}}</li>
  </ul>
  <section class="you">
    <ul>
      <li v-for="(card, index) in MMcards" @click="DIAOchu(card.id)" v-bind:class="[card.id, {open: card.open}]" :key='index' v-bind:title='card.title'>{{card.name}}</li>
    </ul>
    <ul>
      <li v-for="(card, index) in BBcards" v-bind:class="[card.id, {open: card.open}]" :key='index' v-bind:title='card.title'>{{card.name}}</li>
    </ul>
    <ul>
      <li v-for="(card, index) in UScards" v-bind:class="[card.id, {open: card.open}]" :key='index' v-bind:title='card.title'>{{card.name}}</li>
    </ul>
    <ul>
      <li v-for="(card, index) in DDcards" v-bind:class="[card.id, {open: card.open}]" :key='index' v-bind:title='card.title'>{{card.name}}</li>
    </ul>
    <ul class="openCard">
      <li v-for="(card, index) in OPENcards" @click="DIAOdiao(card.id)" v-bind:class="[card.id, {open: card.open}]" :key='index' v-bind:title='card.title'>{{card.name}}</li>
    </ul>
    <ul>
      <li v-for="(card, index) in GPcards" v-bind:class="[card.id, {open: card.open}]" :key='index' v-bind:title='card.title'>{{card.name}}</li>
    </ul>
  </section>
 </div>
</template>

<script>

export default {
  data() {
    return {
      cards: [
        {id: "A1", title: "红桃尖", num: '1', open: false, name: 'A'},
        {id: "A2", title: "红桃二", num: '2', open: false, name: '2'},
        {id: "A3", title: "红桃三", num: '3', open: false, name: '3'},
        {id: "A4", title: "红桃四", num: '4', open: false, name: '4'},
        {id: "A5", title: "红桃五", num: '5', open: false, name: '5'},
        {id: "A6", title: "红桃六", num: '6', open: false, name: '6'},
        {id: "A7", title: "红桃七", num: '7', open: false, name: '7'},
        {id: "A8", title: "红桃八", num: '8', open: false, name: '8'},
        {id: "A9", title: "红桃九", num: '9', open: false, name: '9'},
        {id: "A10", title: "红桃十", num: '10', open: false, name: '10'},
        {id: "A11", title: "红桃勾", num: '11', open: false, name: 'J'},
        {id: "A12", title: "红桃皮蛋", num: '12', open: false, name: 'Q'},
        {id: "A13", title: "红桃老K", num: '13', open: false, name: 'K'},
        {id: "B1", title: "黑桃尖", num: '1', open: false, name: 'A'},
        {id: "B2", title: "黑桃二", num: '2', open: false, name: '2'},
        {id: "B3", title: "黑桃三", num: '3', open: false, name: '3'},
        {id: "B4", title: "黑桃四", num: '4', open: false, name: '4'},
        {id: "B5", title: "黑桃五", num: '5', open: false, name: '5'},
        {id: "B6", title: "黑桃六", num: '6', open: false, name: '6'},
        {id: "B7", title: "黑桃七", num: '7', open: false, name: '7'},
        {id: "B8", title: "黑桃八", num: '8', open: false, name: '8'},
        {id: "B9", title: "黑桃九", num: '9', open: false, name: '9'},
        {id: "B10", title: "黑桃十", num: '10', open: false, name: '10'},
        {id: "B11", title: "黑桃勾", num: '11', open: false, name: 'J'},
        {id: "B12", title: "黑桃皮蛋", num: '12', open: false, name: 'Q'},
        {id: "B13", title: "黑桃老K", num: '13', open: false, name: 'K'},
        {id: "C1", title: "方块尖", num: '1', open: false, name: 'A'},
        {id: "C2", title: "方块二", num: '2', open: false, name: '2'},
        {id: "C3", title: "方块三", num: '3', open: false, name: '3'},
        {id: "C4", title: "方块四", num: '4', open: false, name: '4'},
        {id: "C5", title: "方块五", num: '5', open: false, name: '5'},
        {id: "C6", title: "方块六", num: '6', open: false, name: '6'},
        {id: "C7", title: "方块七", num: '7', open: false, name: '7'},
        {id: "C8", title: "方块八", num: '8', open: false, name: '8'},
        {id: "C9", title: "方块九", num: '9', open: false, name: '9'},
        {id: "C10", title: "方块十", num: '10', open: false, name: '10'},
        {id: "C11", title: "方块勾", num: '11', open: false, name: 'J'},
        {id: "C12", title: "方块皮蛋", num: '12', open: false, name: 'Q'},
        {id: "C13", title: "方块老K", num: '13', open: false, name: 'K'},
        {id: "D1", title: "梅花尖", num: '1', open: false, name: 'A'},
        {id: "D2", title: "梅花二", num: '2', open: false, name: '2'},
        {id: "D3", title: "梅花三", num: '3', open: false, name: '3'},
        {id: "D4", title: "梅花四", num: '4', open: false, name: '4'},
        {id: "D5", title: "梅花五", num: '5', open: false, name: '5'},
        {id: "D6", title: "梅花六", num: '6', open: false, name: '6'},
        {id: "D7", title: "梅花七", num: '7', open: false, name: '7'},
        {id: "D8", title: "梅花八", num: '8', open: false, name: '8'},
        {id: "D9", title: "梅花九", num: '9', open: false, name: '9'},
        {id: "D10", title: "梅花十", num: '10', open: false, name: '10'},
        {id: "D11", title: "梅花勾", num: '11', open: false, name: 'J'},
        {id: "D12", title: "梅花皮蛋", num: '12', open: false, name: 'Q'},
        {id: "D13", title: "梅花老K", num: '13', open: false, name: 'K'},
        {id: "Z1", title: "大王", num: 'Z1', open: false, name: 'JOKER'},
        {id: "Z2", title: "小王", num: 'Z2', open: false, name: 'JOKER'}
      ],
      cardsOld: [],                 //总牌
      MMcards: [],                  //玩家N1的牌
      BBcards: [],                  //玩家N2的牌
      UScards: [],                  //玩家N3的牌
      DDcards: [],                  //玩家N4的牌
      OPENcards: [],                //桌面上翻起的牌
      GPcards: [],                  //桌面上剩下的牌
      FPJSQ: null,                  //发牌计时器
      DiaoQ: {chu: '', diao: '', fuan: ''}     //钓红点-出-钓-计时器
    }
  },
  methods: {
    // 洗牌
    shuffle(arr) {
      var i, j, temp;
      for (i = arr.length - 1; i > 0; i--) {
          j = Math.floor(Math.random() * (i + 1));
          temp = arr[i];
          arr[i] = arr[j];
          arr[j] = temp;
      }
      return arr;
    },
    startCard() {
      this.cards = this.$options.methods.shuffle(this.cards);
      this.$forceUpdate();
      this.ad = !this.ad;
      window.console.log(this.cards)
    },
    //切牌
    cutCard(io) {
      // this.$set(this.cards[io], this.cards.back, false)
      this.cards[io].open = true;
      this.cardsOld = this.cards.splice(0, io);
      window.console.log(this.cardsOld)
      // Object.assign(this.cards,this.cardsOld);
      this.cards = this.cards.concat(this.cardsOld);
      // window.console.log(io)
    },
    // 发牌
    dealCard() {
      this.FPJSQ = setInterval(() => {
        if (this.cards.length == 54 || this.cards.length == 50 || this.cards.length == 46 || this.cards.length == 42 || this.cards.length == 38 || this.cards.length == 34) {
          this.MMcards.unshift(this.cards.pop())
        } else if (this.cards.length == 53 || this.cards.length == 49 || this.cards.length == 45 || this.cards.length == 41 || this.cards.length == 37 || this.cards.length == 33) {
          this.BBcards.unshift(this.cards.pop())
        } else if (this.cards.length == 52 || this.cards.length == 48 || this.cards.length == 44 || this.cards.length == 40 || this.cards.length == 36 || this.cards.length == 32) {
          this.UScards.unshift(this.cards.pop())
        } else if (this.cards.length == 51 || this.cards.length == 47 || this.cards.length == 43 || this.cards.length == 39 || this.cards.length == 35 || this.cards.length == 31) {
          this.DDcards.unshift(this.cards.pop())
        } else if (this.cards.length <= 30 && this.cards.length > 24) {
          this.cards[this.cards.length-1].open = true;
          this.OPENcards.unshift(this.cards.pop())
        } else {
          clearInterval(this.FPJSQ);
        }
      }, 100)
    },
    // 钓牌规则
    DIAOchu(cardID) {
      this.DiaoQ.chu = cardID;
      let thisNum = cardID.replace(/[^0-9]/ig,"");
      if (thisNum < 10) {
        window.console.log(`小得可怜`)

      }
      window.console.log('C' + thisNum)
    },
    DIAOdiao(cardID) {
      this.DiaoQ.diao = cardID;
      window.console.log(`D${this.DiaoQ.diao}`);
      // if (this.DiaoQ.chu ) {
        
      // }
    },
    DIAOqi(cardID) {
      this.DiaoQ.qi = cardID;
      window.console.log('Q' + this.DiaoQ.qi)
    },
    DIAOCard() {
      this.DiaoQ.qi = this.MMcards.num;
      if (this.DiaoQ.qi === '') {
        this.DiaoQ.diao = this.MMcards.num
      }
      window.console.log('H' + this.DiaoQ.qi)
      window.console.log('G' + this.DiaoQ.diao)
      // switch (this.cards.num) {
      //   case value:
          
      //     break;
      
      //   default:
      //     break;
      // }
    }
  }
  // computed: {
  //   openCard() {
  //     return { open: this.cards.back }
  //   }
  // }
}
</script>

<style lang="scss" scoped>
$bodyColor: #f60;
ul.openCard {background: $bodyColor}

</style>
