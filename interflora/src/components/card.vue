<template>
  <div>
                <List greetingsCollection={this.greetings} />
                <form>
                    <div className="form-components">
                      <textarea class="form-control" cols="50" rows="4" placeholder="Write a greeting" v-model="textBoxInput" @keyup="textChanged"></textArea>
                        
                        <select value={this.state.category} name="category" onChange={this.changeHandler}>
                            <option value="choose_category" disabled>Choose category</option>
                            <option value="category1">Valentine's Day</option>
                            <option value="category2">Happy B'day</option>
                            <option value="category3">Happy Anniversary</option>
                            <option value="category4">Father's Day</option>
                        </select>
                    </div>
                    <div className="form-control">
                        <button className="button" onClick={this.submitHandler}>Add Greeting</button>
                    </div>
                </form>
            </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
