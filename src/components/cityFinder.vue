

<template>  
    <div class="test">
        <div class="finder-box">
            <h1 class="text-center">Where's that postcode?</h1>
            
            <div class="row">
                <div class="col-md-12">
                    <input v-model="postcode" v-on:keyup.enter="lookupCity" type="text" class="form-control" placeholder="Enter a postcode...">
                </div>

                <div class="col-md-12">
                    <button v-on:click="lookupCity" class="find-button btn btn-primary btn-block">Find city</button>
                </div>
                <div class="col-md-12">
                    <p class="city"> {{ city }} </p>
                    <p v-show="!postcodeValidation" class="error"> {{ postcodeError }} </p>
                </div>
            </div>
        </div> 
    </div>
</template>

<script>

export default {
  name: 'cityFinder',
  data() {
    return {
        postcode: '',
        city: '',
        postcodeValidation: true,
        postcodeError: 'A postcode must be at least 5 digits long. Please try again.'
    }
  },
  computed: {
    postcodeApiString: function() {
        return 'http://ZiptasticAPI.com/' + this.$data.postcode;
        console.log(postcodeApiString);
    }
  },
  methods: {
      lookupCity: function () {
          this.postcodeValidation = true;
          if (this.$data.postcode.length == 5) {
              this.$data.city = 'searching...';
              axios.get(this.postcodeApiString).then(response => {
                  this.$data.city = `${response.data.city}, ${response.data.state}`;
              })
          } else {
              this.$data.city = '';
              this.postcodeValidation = false;
          }
      }
  }
}

</script>


<style>
  .finder-box {
    background-color: rgba(255, 255, 255, 0.6);
    border-radius: 5px;
    padding: 10px 50px 30px 50px;
    margin-top: 100px;
  }

h1 {
    margin-bottom: 50px;
}

  p {
    margin-left: 5px;
  }
  
  .city {
    color: #444;
    font-size: 27px;
    font-weight: bold;
  }

  .error {
      color: darkred;
      font-size: 15px;
  }

  .form-control {
    margin-bottom: 10px;
  }

  .find-button {
    margin: 25px auto 40px auto;
    color: #fff;
    background-color: #33b797;
    border-color: #33b797;
  }

 .find-button:focus {
      outline: none;
  }

</style>