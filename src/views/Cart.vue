<template>
  <div>
                    <h1 class="text-center" v-text="sitename2"></h1>


                    <br><br><br>
                <div class="container ">
                    <div class="row">

                        <div v-for="lessons in cart" :key="lessons.id" class="col-md-4 mb-5 col-sm-12 d-block mx-auto">
                            <div class="card "
                                style="width: 18rem;border-bottom-width: 5px; border-bottom-color:#0188cc;">
                                <img height="200" v-bind:src="lessons.image">
                                <div class="card-body">
                                    <h5 class="card-title">Subject : {{lessons.subject}}</h5>
                                    <p class="card-text"> Location : {{lessons.location}} </p>
                                    <p> <b>Price : ${{lessons.price}}</b></p>
                                    <!-- <p class="text-success">Available Spaces : {{lessons.availablespace - cartCount(lessons.id)}}</p> -->

                                    <button style="float: center;" href="#" class="btn btn-primary"
                                        v-on:click='del(lessons, cart)'>Remove from Cart</button>

                                    <br>
                                    <div>

                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                    </div>

                    <center>
                        <h2>Checkout</h2>
                        <br>
                        <form>

                            <input class="form-control" style="width: 60%;" type="text" v-model="order.name"
                                placeholder="Enter Your Name" required><br>
                            <input class="form-control" style="width: 60%;" type="number" v-model="order.number"
                                placeholder="Enter Your Phone Number" required><br>

                            <!-- <input style="margin-bottom: 50px;" class="btn btn-primary" type="submit"
                                value="Place Order" hidden> -->

                            <!-- <p class="bg-danger"> Please input a valid
                                name</p> -->


                            <input style="margin-bottom: 50px;" class="btn btn-primary" type="submit" value="Place Order">
                        </form>

                        <!-- <p>{{order.name}}</p>
                        <p>{{order.number}}</p>
                        <div v-for="tings in purchase">
                            <p>{{tings.availablespace}}</p>
                            <p>{{tings._id}}</p>
                        </div> -->
                    </center>

        </div>
</template>

<script>
export default {
  
  setup() {
    
  },

  props:['cart'],

  data(){
    return{

        sitename2: "Cart And Checkout",

      

      order:{
        name:"",
        number:'',
      }
    }
  },

methods:{
  del(lessons, cart){
this.$emit('delete', lessons, cart)
  }

}
}
</script>
