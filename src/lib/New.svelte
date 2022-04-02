<script>
  import {app,db} from './config.svelte';
    import { addDoc,collection } from "https://www.gstatic.com/firebasejs/9.6.10/firebase-firestore.js";
  let title;
  let body
async function handleSubmit(e){
 if(title === undefined || body === undefined){
  alert('please Enter a Title and Body')
  return
 }
 else{
  try{
    const docRef = await addDoc(collection(db, "blogs"), {
  title,
  body,
});
    alert('Blog Posted Successfully')
  }
  catch(e){
    alert('ERROR',e)
  }

 }
}
console.log(app)
</script>

<h5 class="center-align">Make a New Guide</h5>

  <div class="row" on:submit={handleSubmit} >
    <form class="col s12">
      <div class="row container">
        <div class="input-field col s12 l12">
          <i class="material-icons prefix">Title</i>
          <input id="icon_prefix" type="text" class="validate" bind:value={title} >
          <label for="icon_prefix">Title</label>
        </div>
        <div class="input-field col s12 l12">
          <i class="material-icons prefix">body</i>
          <input id="icon_telephone" type="tel" class="validate"  bind:value={body}>
          <label for="icon_telephone">Body</label>
        </div>
        <button class="btn blue">Submit</button>
        
      </div>
    </form>
  </div>
