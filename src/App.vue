<template>
  <h1>Soap Make</h1>
  <div class="wrapper">
    <form @submit ="registerAnswer">
    <label for="soap">Categories:</label>
    <select  v-model="soapSelected" id="soap">
      <option disabled value="">Please select one</option>
      <option value="glycerinSoap" @click="GlycerinSoap">Glycerin Soap</option>
      <option value="guessSoap" @click="GuessSoap" >Guess Soap</option>
    </select>
    <input type="submit" value="Submit">
  </form>
      <!-- searchbar -->
      <div class="searchbar">
        <input v-model="searchProductsInput" @input="searchProducts" placeholder="Search Soap...">
      </div>
    </div>
    <div class="row" v-if="filteredProducts().length">
      <div class="prodCard" v-for="product in filteredProducts()" :key="product.id">


        <!-- body -->
        <div class="card-body">
          <img :src="product.img" :alt="product.prodName" loading="lazy" @mouseenter="onMouseEnter"
            @mouseleave="onMouseLeave">
          <h3>{{ product.make }}</h3>
          <h3>{{ product.Categories }}</h3>

        </div>
        <!-- footer -->
        <div class="card-footer">
          <p :class="product.amount > 420 ? 'expensive' : 'cheap'">R{{ product.amount.toFixed(2) }}</p>
        </div>
      </div>
    </div>
</template>


<script>
export default {
  name: 'ProductsComp',
  data() {
    return {
      soapSelected: '',
      searchProductsInput: '',
      products: [
        {
          "id": 1,
          "name": "Luxury Artisan Handmade Soaps",
          "make": " Lavender fields ",
          "Categories": "Glycerin Soap",
          "amount": 55,
          "img": "https://i.postimg.cc/28QgBc5r/ed929619-a18f-484e-9543-6b401a5df5c5.jpg",
        },
        {
          "id": 2,
          "name": "Luxury Artisan Handmade Soaps",
          "make": "Espresso aroma ",
          "Categories": "Guest Soap",
          "amount": 45,
          "img": "https://i.postimg.cc/MKnv6BZ7/97222de9-ff18-487e-a3d4-6b67901dc366.jpg",
        },
        {
          "id": 3,
          "name": "Luxury Artisan Handmade Soaps",
          "make": "Beaumont Allure",
          "Categories": "Guest Soap",
          "amount": 70,
          "img": "https://i.postimg.cc/v830RJD1/bd5b3354-1884-4590-8e35-a38694c0802c.jpg",
        },
        {
          "id": 4,
          "name": "Luxury Artisan Handmade Soaps",
          "make": "Jasmine Blossom ",
          "Categories": "Glycerin Soap",
          "amount": 50,
          "img": "https://i.postimg.cc/gcXDxNDj/a6d62e2e-beef-45fb-a1cf-cd0f4a3913c3.jpg",
        },
        {
          "id": 5,
          "name": "Luxury Artisan Handmade Soaps",
          "make": " Milk-way Express ",
          "Categories": "Glycerin Soap",
          "amount": 80,
          "img": "https://i.postimg.cc/7LWRZvwr/photo-1607006411601-775c8cc632dc-blend-000000-blend-alpha-10-blend-mode-normal-blend-w-1-crop-faces.jpg",
        },
        {
          "id": 6,
          "name": " Luxury Artisan Handmade Soaps",
          "make": "Couple love",
          "Categories": "Guest Soap",
          "amount": 120,
          "img": "https://i.postimg.cc/CxRZBsXn/s-l1200.jpg",
        },
        {
          "id": 7,
          "name": "Luxury Artisan Handmade Soaps",
          "make": "Lemon-grass ",
          "Categories": "Guest Soap",
          "amount": 80,
          "img": "https://i.postimg.cc/PT7KKXQh/7-cc45b47e-d917-45c5-8957-387f24ad8c3d-1080x.jpg",
        },
        {
          "id": 8,
          "name": " Luxury Artisan Handmade Soaps",
          "make": "Pomegranate",
          "Categories": "Glycerin Soap",
          "amount": 80,
          "img": "https://i.postimg.cc/FzRNRcxs/5-cfe20186-e3d1-446d-bf80-61e5e8564131-1080x.jpg",
        }

      ]
    }
  },
  methods: {
    filteredProducts() {
      // return this.products.filter(product => product.make.toLowerCase().includes(this.searchProductsInput.toLowerCase()));
      // alert(this.soapSelected)
      if( this.soapSelected == 'glycerinSoap' ){
        return this.products.filter((product)=>{
          return product.Categories == "Glycerin Soap";
        });
      } else if(this.soapSelected== 'Guest Soap' ){
        return this.products.filter((product)=>{
          return product.Categories == "Guest Soap";
        });
      }
      return this.products
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.wrapper :is(.row) {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.prodCard {
  width: 18rem;
}

.prodCard :is(>*, img) {
  width: 100%;
  aspect-ratio: 1/1;
}

.expensive {
  font-weight: bolder;
  color: darkkhaki;
}

.cheap {
  color: black;
}
</style>
