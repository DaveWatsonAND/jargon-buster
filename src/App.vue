<template>


<p v-html="jargonBustedString"></p>
</template>

<script>




export default {
  name: 'App',
  mounted(){
    this.description.forEach((word)=>{
      return document.querySelectorAll(`[id=${word.id}]`).forEach((ele)=>ele.addEventListener('click',this.clickTest))
    })
  },

  methods:{
    clickTest(event){
        this.activeWord = (this.description.find((val)=>val.id == [event.target.id])).description
        alert(this.activeWord)
    }
  },
  
  data() {
  return {
      text:"This is a test which includes a test-case for the demo, this is a sentence",
      description:[
          {word:"test",description:"this is a test description for the word test", id:"testid"},
          {word:"test-case",description:"this is a is description for the word test case", id:"testCaseId"},
          {word:"this is a sentence",description:"this is a is description for the test sentence",id:"sentenceId"}
          ],
      activeWord:'',
}

},
computed:{
jargonBustedString(){
  this.description.map(word=>{
      this.text =this.text.replace(word.word,`<a id=${word.id} id="tooltip-button">${word.word}</a>`)
      console.log(this.text)
    })

    return this.text
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
a{
  font-weight: bold;
  text-decoration: underline;
}
</style>
