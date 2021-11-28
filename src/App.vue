<template>
  <div class="page">
    <div>
      <div class='block1'>
        <div class='block1__header'>Alina’s shop</div>
        <div class='section1__buttons'>
          <div><button class='section1__button' @click="loadDataBlush()">Blush</button></div>
          <div><button class='section1__button' @click="loadDataBronzer()">Bronzer</button></div>
        </div>
      </div>
    </div>
    <div class='block2'>
      <div class='section2'> 
        <div class='section2__text'>Filter’s</div>
        <div class='hypoallergenic'>Hypoallergenic</div>
        <div class='hypoallergenic'>Hypoallergenic</div>
        <div class='hypoallergenic'>Hypoallergenic</div>
      </div>
      <div class='cards'>
        <Card @click.native="showNewPage = true"
          v-for="product in products" :key="product.id" 
          :item="product"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Card from '@/components/Card.vue'
import axios from 'axios'
export default {
  name: 'App',
  components: {
    Card
  },
  data() {
    return {
      products: []
    }
  },
  mounted() {
    this.loadDataBlush()
  },
  methods: {
    loadDataBronzer() {
      this.products.splice(0, this.products.length)
      axios({
        method: 'get',
        url: 'http://makeup-api.herokuapp.com/api/v1/products.json?product_type=bronzer'  
      })
        .then((response) => {
          console.log(response)
          this.products.push(...response.data)
        })
        .catch((error) => {
          console.log(error)
        })
    },
    loadDataBlush() {
      this.products.splice(0, this.products.length)
      axios({
        method: 'get',
        url: 'http://makeup-api.herokuapp.com/api/v1/products.json?product_type=blush'  
      })
        .then((response) => {
          console.log(response)
          this.products.push(...response.data)
        })
        .catch((error) => {
          console.log(error)
        })
    }
  }
}
</script>

<style lang="scss" scoped>
  .page{
    display: grid;
    grid-template-columns: 200px 1fr;
    padding: 35px;
  }
  .section1{
    color: #2264D1;
    font-size: 24px;
  }
  .block1{
    display: flex;
    align-items: center;
    text-align: center;
    flex-direction: column;
    margin-top: 40px;
    padding-right: 13px;
    position: sticky;
    top: 45px;
  }
  .block1__header{
    color: #2264D1;
    font-weight: bold;
    font-size: 24px;
}
  .section1__button{
    margin-top: 18px;
    border: 1px solid #9DC2FF;
    box-sizing: border-box;
    border-radius: 8px;
    width: 187px;
    height: 49px;
    color: #2264D1;
    font-weight: bold;
    font-size: 15px;
    cursor: pointer;
  }
  .section1__button:hover {
    box-shadow: 6px 24px 34px rgb(0 0 0 / 10%), 3px 9px 14px rgb(0 0 0 / 9%);
}
  .section1__buttons{
    padding-top: 35px;
  }
  .section1{
    display: grid;

  }
  .hypoallergenic{
    background: #EDEDF0;
    border-radius: 99px;
    width: 120px;
    height: 32px;
    color: #4A4B57;
    display: flex;
    text-align: center;
    justify-content: center;
    padding-top: 12px;
    padding-left: 4px;
    margin: 0px 12px;
    cursor: pointer;
  }
  .section2{
    display: flex;
  }
  .section2__text{
    padding-top: 13px;
  }
  .cards{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-gap: 40px;
    padding-top: 40px;
  }
</style>
