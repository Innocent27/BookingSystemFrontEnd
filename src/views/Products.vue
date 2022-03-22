<template>
  <div class="container d-flex justify-content-end mb-3 mt-5 pt-4">
     <div class="d-flex w-25 ms-3">
      <label for="" class="form-label">Sort by category</label>
      <select class="form-select" name="" id="sortCategory" onchange="sortCategory()">
        <option value="All">All</option>
        <option value="WesternCape">Western Cape</option>
        <option value="Gauteng">Gauteng</option>
        <option value="EasternCape">Eastern Cape</option>
      </select>
    </div> 

    <div class="d-flex w-25 ms-3">
      <label for="" class="form-label">Sort by name</label>
      <select class="form-select" name="" id="sortName" onchange="sortName()">
        <option value="ascending">Ascending</option>
        <option value="descending">Descending</option>
      </select>
    </div> 
    <div class="d-flex w-25 ms-3">
      <label for="" class="form-label">Sort by price</label>
      <select class="form-select" name="" id="sortPrice" onchange="sortPrice()">
        <option value="ascending">Ascending</option>
        <option value="descending">Descending</option>
      </select>
    </div>  
    <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#exampleModal">Add a product</button>
    <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#exampleModal2">Update user <i class="bi bi-person-circle"></i></button>
    <router-link class="btn btn-primary" to="/Cart">Cart</router-link>
   </div>
  <!-- <br />
  <hr />  -->
  <!-- Button trigger modal -->

  <!-- Modal to create products -->
  <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close" ></button>
        <div class="modal-body">
          <div class="modal-content">
            <div class="modal-body">
              <div class="mb-3">
                <label for="addTitle" class="form-label">Title</label>
                <input class="form-control" type="text" name="addTitle" id="addTitle" v-model="title" />
              </div>
              <div class="mb-3">
                <label for="" class="form-label">Category</label>
                <select class="form-select" name="addCategory" id="addCategory" v-model="category">
                  <option value="WesternCape">Western Cape</option>
                  <option value="Gauteng">Gauteng</option>
                  <option value="EasternCape">Eastern Cape</option>
                </select>
              </div>
              <div class="mb-3">
                <label for="addPrice" class="form-label">Price</label>
                <input class="form-control" type="text" name="addPrice" id="addPrice" v-model="price"/>
              </div>
              <div class="mb-3">
                <label for="addImg" class="form-label">Image URL</label>
                <input class="form-control" type="text" name="addImg" id="addImg" v-model="img"/>
              </div>
              <div class="mb-3">
                <label for="addDescription" class="form-label">Description</label> 
                <input class="form-control" type="text" name="addDescription" id="addDescription" v-model="description"/>
              </div>
            </div>

            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
            <br />
            <button type="button" class="btn btn-primary" data-bs-dismiss="modal" @click="createProduct()">Create Product</button>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- modal to update the user -->

  <div class="modal fade" id="exampleModal2" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        <div class="modal-body">
          <div class="modal-content">
            <div class="modal-body">
              <div class="mb-3">
                <label for="addFullname" class="form-label">Fullname</label>
                <input class="form-control" type="text" name="addFullname" id="addFullname" v-model="fullname"/>
              </div>
              <div class="mb-3">
                <label for="addEmail" class="form-label">Email</label>
                <input class="form-control" type="email" name="addEmail" id="addEmail" v-model="email"/>
              </div>
              <div class="mb-3">
                <label for="addPhone_number" class="form-label">Phone_number</label>
                <input class="form-control" type="text" name="addPhone_number" id="addPhone_number" v-model="phone_number"/>
              </div>
              <div class="mb-3">
                <label for="addPassword" class="form-label">Password</label>
                <input class="form-control" type="password" name="addPassword" id="addPassword" v-model="password"/>
              </div>
            </div>

            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
            <br />
            <button type="button" class="btn btn-primary" data-bs-dismiss="modal" @click="updateUser()">Update User</button>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- modal to update products -->

  <div class="modal fade" id="exampleModal3" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
    <div class="modal-dialog">
      <div class="modal-content">
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        <div class="modal-body">
          <div class="modal-content">
            <div class="modal-body">
              <div class="mb-3">
                <label for="addTitle" class="form-label">Title</label>
                <input class="form-control" type="text" name="addTitle" id="addTitle" v-model="title"/>
              </div>
              <div class="mb-3">
                <label for="" class="form-label">Category</label>
                <select class="form-select" name="addCategory" id="addCategory" v-model="category">
                  <option value="WesternCape">Western Cape</option>
                  <option value="Gauteng">Gauteng</option>
                  <option value="EasternCape">Eastern Cape</option>
                </select>
              </div>
              <div class="mb-3">
                <label for="addPrice" class="form-label">Price</label>
                <input class="form-control" type="text" name="addPrice" id="addPrice" v-model="price" />
              </div>
              <div class="mb-3">
                <label for="addImg" class="form-label">Image URL</label>
                <input class="form-control" type="text" name="addImg" id="addImg" v-model="img"/>
              </div>
              <div class="mb-3">
                <label for="addDescription" class="form-label" >Description</label>
                <input class="form-control" type="text" name="addDescription" id="addDescription" v-model="description"/>
              </div>
            </div>

            <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">
              Close
            </button>
            <br />
            <button type="button" class="btn btn-primary" data-bs-dismiss="modal" @click="updateBooking()">Edit Product</button>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="container my-5">
    <!-- <input type="text" v-model="search" /> -->
    <div v-if="products.length" class="row">
      <div v-for="product of filterProducts" :key="product._id" class="col-lg-4 col-md-6 col-sm-12">
        <div class="card">
          <img :src="product.img" class="card-img-top" :alt="product.title"/>
          <div class="card-body">
            <h5 class="card-title">{{ product.title }}</h5>
            <p class="card-text">R{{ product.price }}</p>
            <p class="card-text">{{ product.category }}</p>
            <p class="card-text">{{ product.description }}</p>
            <p class="card-text">{{ product._id }}</p>
            <div class="d-flex mb-3">
              <input type="number" class="form-control" value="1" min="1" id="addToCart${position}"/>
              <button type="button" class="btn2" @click="addToCart()">
                <i class="fas fa-cart-plus"></i>
              </button>
            </div>
          </div>
          <div class="d-flex justify-content-end card-footer">
            <button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#exampleModal3">Edit</button>
            <button type="button" class="btn btn-danger w-50 ms-3" @click="deleteProduct()">Delete</button>
          </div>
        </div>
      </div>
    </div>
    <div v-else>
      <p>Loading products...</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      bookings: [],
      hotel_name: "",
      check_in: "",
      check_out: "",
      description: "",
      img: "",
      description: "",
      price: "",
      search: "",
    };
  },
  mounted() {
    if (localStorage.getItem("jwt")) {
      fetch("https://bookingsystemapp.herokuapp.com/bookings/", {
        method: "GET",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          this.bookings = json;
        })
        .catch((err) => {
          alert("User not logged in");
        });
    } else {
      alert("User not logged in");
      this.$router.push({ name: "Login" });
    }
  },
  computed: {
    filterBookings: function () {
      return this.bookings.filter((booking) => {
        return booking.hotel_name.match(this.search);
      });
    },
  },
  methods: {
    // Create Booking
    createProduct() {
      if (!localStorage.getItem("jwt")) {
        alert("User not logged in");
        return this.$router.push({ name: "Login" });
      }
      fetch("https://bookingsystemapp.herokuapp.com/bookings", {
        method: "POST",
        body: JSON.stringify({
          hotel_name: this.hotel_name,
          check_in: this.check_in,
          check_out: this.check_out,
          description: this.description,
          img: this.img,
          price: this.price,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          alert("Booking Created");
          this.$router.push({ name: "Products" });
        })
        .catch((err) => {
          alert(err);
        });
    },
    // Update Product
    updateBooking() {
      if (!localStorage.getItem("jwt")) {
        alert("User not logged in");
        return this.$router.push({ name: "Login" });
      }
      fetch("https://bookingsystemapp.herokuapp.com/bookings" , {
        method: "PUT",
        body: JSON.stringify({
          hotel_name: this.hotel_name,
          check_in: this.check_in,
          check_out: this.check_out,
          description: this.description,
          img: this.img,
          price: this.price,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          alert("Product Updated");
          this.$router.push({ name: "Products" });
        })
        .catch((err) => {
          alert(err);
        });
    },
    // Update User
    updateUser() {
      if (!localStorage.getItem("jwt")) {
        alert("User not logged in");
        return this.$router.push({ name: "Login" });
      }
      fetch("https://bookingsystemapp.herokuapp.com/users" + this.id, {
        method: "PUT",
        body: JSON.stringify({
          fullname: this.fullname,
          email: this.email,
          password: this.password,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          alert("User Updated");
          this.$router.push({ name: "Products" });
        })
        .catch((err) => {
          alert(err);
        });
    },
    // // Delete Product
    deleteProduct() {
      if (!localStorage.getItem("jwt")) {
        alert("User not logged in");
        return this.$router.push({ name: "Login" });
      }
      fetch("https://bookingsystemapp.herokuapp.com/bookings/" + this._id, {
        method: "DELETE",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((json) => {
          alert("Product Deleted");
          this.$router.push({ name: "Products" });
        })
        .catch((err) => {
          alert(err);
        });
    },
  },
};
</script>