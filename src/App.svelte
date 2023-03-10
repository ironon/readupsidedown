<script lang="ts">
  import "./app.css"
  import words from "./assets/top1000.json"
  import {
  sentence,
  addNouns
} from 'txtgen'

  let word: any = "david is cool"
  let input = ""
  let type = "word"
  addNouns(["David", "Ethan", "Easton", "Cameron", "Jess", "tuskytime.org", "bananas"])
  function setNewWord() {
    word = getNewWord()
  }
  function checkAnswer(){
    if (input == word) {
      word = getNewWord()
      input = ""
      
    }
  }
  function repeat(func, num) {
    let text = ""
    for (let i = 0; i < num; i++) {
      text += func() + " "
    }
    return text
  }
  function getNewWord() {
    switch(type) {
      case "word":
        return words[Math.round(Math.random() * words.length)]
      case "sentence":
        return sentence()
      case "paragraph":
        return repeat(sentence, 4)
    }
  }
</script>


<div id="main">
  <h1>LEARN TO READ UPSIDE-DOWN</h1>
  <p>apparently everybody learned at somepoint besides me f isbdgfdhsuifsdyx</p>
  <div id="centered">
    <p id="word">{word}</p>
    <input id="inputword" bind:value={input} on:input={checkAnswer} type="text">
    <select bind:value={type} on:change={setNewWord} id="type">
      <option value="word">Word</option>
      <option value="sentence">Sentence</option>
      <option value="paragraph">Paragraph</option>
    </select>
  </div>
</div>

<style>
  #main {
    width: 100%;
    height: 100%;
    margin: 0;
    display: flex;
    justify-content: top;
    align-items: center;
    flex-direction: column;
    background: radial-gradient(#f1dcaf, rgb(240, 231, 203))
  }
  #centered {
    width: 100%;
    height: 90%;
    display: flex;
    justify-content: center;
    flex-direction: column;
    align-items: center;
  }
  #word {
    transform: rotate(180deg);
    width: 70%;
    text-align: center;
    font-size: 2rem;
  }
  #inputword{
    margin-bottom: 1rem;
    padding: 3vmin;
    background-color: #e5ca90;
    border: 2px solid #8d7237;
  }
  #type {
    background-color: #e5ca90;
    border: 2px solid #8d7237;
    
  }
</style>