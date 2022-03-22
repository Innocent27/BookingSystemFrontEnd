<template>
<!-- <body id="page-top"> -->
<!-- cards -->
 <header class="masthead">
            <div class="container">
                <div class="masthead-subheading">Welcome To Our LNM Hotels & Resorts
                </div>
                <div class="masthead-heading text-uppercase">It's Nice To Meet You</div>
                <a class="btn btn-primary btn-xl text-uppercase" href="#services">Please book to get special deals &#128514;</a>
            </div>
</header>
<!-- </body> -->
</template>
<style scoped>
header.masthead {
  padding-top: 10.5rem;
  padding-bottom: 6rem;
  text-align: center;
  color: #fff;
  background-image: url("https://i.postimg.cc/Pfpq1WJK/las-vegas-1846684-340.jpg");
  background-repeat: no-repeat;
  background-attachment: scroll;
  background-position: center center;
  background-size: cover;
}
@media (min-width: 768px) {
  header.masthead {
    padding-top: 17rem;
    padding-bottom: 12.5rem;
  }
  header.masthead .masthead-subheading {
    font-size: 2.25rem;
    font-style: italic;
    line-height: 2.25rem;
    margin-bottom: 2rem;
  }
  header.masthead .masthead-heading {
    font-size: 4.5rem;
    font-weight: 700;
    line-height: 4.5rem;
    margin-bottom: 4rem;
  }
}
@media (min-width: 576px) {
	.container-sm,
	.container {
		max-width: 540px;
	}
}
@media (min-width: 768px) {
	.container-md,
	.container-sm,
	.container {
		max-width: 720px;
	}
}
@media (min-width: 992px) {
	.container-lg,
	.container-md,
	.container-sm,
	.container {
		max-width: 960px;
	}
}
@media (min-width: 1200px) {
	.container-xl,
	.container-lg,
	.container-md,
	.container-sm,
	.container {
		max-width: 1140px;
	}
}
@media (min-width: 1400px) {
	.container-xxl,
	.container-xl,
	.container-lg,
	.container-md,
	.container-sm,
	.container {
		max-width: 1320px;
	}
}

</style>
<script>
export default {
  data() {
    return {
      name: "",
      email: "",
      phone_number: "",
      password: "",
    };
  },
  methods: {
    register() {
      fetch("https://bookingsystemapp.herokuapp.com/users", {
        method: "POST",
        body: JSON.stringify({
          name: this.name,
          email: this.email,
          phone_number: this.phone_number,
          password: this.password,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })
        .then((response) => response.json())
        .then((json) => {
          alert("User registered");
          localStorage.setItem("jwt", json.jwt);
          this.$router.push({ name: "Profile" });
        })
        .catch((err) => {
          alert(err);
        });
    },
  },
};
</script>