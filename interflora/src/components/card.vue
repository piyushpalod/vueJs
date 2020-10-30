<template>

    <div class="vue-tempalte container">
      <form id="app" @submit="checkForm">
        <div class="form-components">
          <textarea
            class="form-control form-control-lg"
            cols="50"
            rows="4"
            placeholder="Write a greeting"
            v-model="textBoxInput"
            id="textBoxInput"
            v-on:blur="textChanged"
            @keyup="textChanged"
          ></textarea>

          <select v-if="textBoxInput.length > 0" class="form-control form-control-lg mt-5" v-model="categoryList" v-on:change="clearCategory">
            <option v-bind:key="option.value" v-for="option in categories">{{ option.name }}</option>>
          </select>

          <input v-if="categoryList === 'choose your own' " class="form-control form-control-lg mt-5" id="category" type="text" v-model="category" 
          placeholder="Write a category">
        </div>
        <div>
          <button class="btn btn-dark btn-lg btn-block mt-5" v-on:click="saveCard">Add Greeting</button>
        </div>
      </form>

      <div class="saved-cards">
                <h2>Your saved cards</h2>
                <span v-if="savedCards.length === 0">{{ noSavedCards }}</span>
                <ul>
                    <li v-for="(value, index) in savedCards"  v-bind:key="index" v-html="value">
                    </li>
                </ul>
      </div>
    </div>
</template>

<script>
export default {
  name: "greetingCard",
  props: {
    msg: String,
  },
  data() {
        return {
            textBoxInput: "",
            noSavedCards: "You have no cards saved",
            category: "",
            categoryList: "",
            categories: [
                {value: "birthday", name: "Happy Birthday"},
                {value: "fathersday", name: "Happy Father's day"},
                {value: "graduation", name: "Happy Graduated"},
                {value: "mothersday", name: "Happy Mother's day"},
                {value: "easter", name: "Happy Easter"},
                {value: "choose your own", name: "choose your own"},
            ],
            savedCards: [],
        }
        },
  methods:{
    checkForm:function(e) {
      //if(this.textBoxInput && this.categoryList) return true;
      this.errors = [];
      if(!this.textBoxInput) this.errors.push("Message required.");
      if(!this.categoryList) this.errors.push("category required.");
      e.preventDefault();
    },
     saveCard() {
            let category = this.category != '' ? this.category : this.categoryList;

            this.savedCards.push('<b>Card #' + (this.savedCards.length + 1) + ': </b>"' + this.textBoxInput + '" [' + category + ']');
        },
  },
  
};
</script>
