<template>
  <div>

            <h1 class="text-center" v-text="name"></h1>


            <br><br><br>

            <aside>
                <p><b>Sort by</b></p>
                <input type="radio" id="subject" v-model="sort.sortingMethod" value="subject">
                <label for="subject">Subject</label><br>

                <input type="radio" id="location" v-model="sort.sortingMethod" value="location">
                <label for="location">Location</label><br>

                <input type="radio" id="price" v-model="sort.sortingMethod" value="price">
                <label for="price">Price</label><br>

                <input type="radio" id="availability" v-model="sort.sortingMethod" value="availablespace">
                <label for="price">Availability</label>

                <br> <br><br>

                <p><b>Sort Order</b></p>
                <input type="radio" id="ascending" name="sort_order" v-model="sort.sortingOrder" value="ascending">
                <label for="ascending">Ascending</label><br>
                <input type="radio" id="descending" name="sort_order" v-model="sort.sortingOrder" value="descending">
                <label for="descending">Descending</label><br>


            </aside>

            <div class="row">

                <div v-for="lessons in lesson" :key="lessons.id" class="col-md-6 col-lg-4 mb-5">
                    <div class="card " style="width: 18rem;border-bottom-width: 5px; border-bottom-color:#0188cc;">
                        <img height="200" v-bind:src="lessons.image">
                        <div class="card-body">
                            <h5 class="card-title">Subject : {{lessons.subject}}</h5>
                            <p class="card-text"> Location : {{lessons.location}} </p>
                            <p> <b>Price : ${{lessons.price}}</b></p>
                            <p class="text-danger" v-if="lessons.availablespace === 0 "> Completely
                                Booked</p>
                            <!-- <p class="text-danger" v-else-if="lessons.availablespace - cartCount(lessons.id) < 5"> Limited stock Only {{lessons.availablespace - cartCount(lessons.id)}} left!</p> -->
                            <p class="text-success" v-else>Available Spaces : {{lessons.availablespace}}</p>

                            <!-- <p class="text-success" v-else>Available Spaces : {{lessons.availablespace -
                                    cartCount(lessons)}}</p> -->

                            <button style="float: right;" href="#" class="btn btn-primary"
                                v-on:click='cartAdd(lessons, lessons.id)' v-if='canAddToCart(lessons)'>Add
                                To
                                Cart</button>
                            <button hidden style="float: right;" href="#" class="btn btn-primary" v-else>Add To
                                Cart</button>



                            <br>
                            <div>
                                <!-- <p>
                    <span v-for="n in lessons.rating">★</span>
                    <span v-for="n in 5 - lessons.rating">☆</span>
                </p> -->
                            </div>
                        </div>
                    </div>
                </div>

            </div>
        </div>
</template>

<script>
// @ is an alias to /src


export default {
  
  props:['lesson', 'cart'],
  data(){
    return{
        name: 'Week 20 Group CourseWork',
showProd:true,

sort: {
                    sortingMethod: "location",
                    sortingOrder: "ascending",
                },

                


    }
  },

  methods:{
      canAddToCart: function (lessons) {
                    return lessons.availablespace > 0;
                    // return lessons.availablespace > this.cartCount(lessons);
                },

                cartAdd(lessons, id){
                    this.$emit('add', lessons, id)
                }
  },

  
  components: {
    
  }
}
</script>

<style>
        aside {
            width: 20%;
            height: 948px;
            padding-left: 15px;
            padding-bottom: 15px;
            padding-top: 15px;
            
            float: left;
            
            background-color: lightgray;
        }
    </style>
