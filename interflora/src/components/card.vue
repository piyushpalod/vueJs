<template>
    <div class="vue-tempalte container">
      <form id="app" @submit="checkForm" action="/something" method="post">
        <div class="form-components">
          <textarea
            class="form-control form-control-lg"
            cols="50"
            rows="4"
            placeholder="Write a greeting"
            v-model="textBoxInput"
            id="textBoxInput"
            @keyup="textChanged"
          ></textarea>

          <select class="form-control form-control-lg mt-5" v-model="category" name="category" id="category">
            <option value="" disabled>Choose category</option>
            <option value="category1">Valentine's Day</option>
            <option value="category2">Happy B'day</option>
            <option value="category3">Happy Anniversary</option>
            <option value="category4">Father's Day</option>
          </select>
        </div>
        <div>
          <button class="btn btn-dark btn-lg btn-block mt-5" type="submit">Add Greeting</button>
        </div>
      </form>
    </div>
</template>

<script>
export default {
  name: "greetingCard",
  props: {
    msg: String
  },
  methods:{
    checkForm:function(e) {
      if(this.textBoxInput && this.category) return true;
      this.errors = [];
      if(!this.textBoxInput) this.errors.push("Message required.");
      if(!this.category) this.errors.push("category required.");
      e.preventDefault();
    }
  }
};
</script>
