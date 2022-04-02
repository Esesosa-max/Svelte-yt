<script>
  import logo from './assets/svelte.png'
   const tabs = ['Make New Guide','Home' ,]
   let currentTabs = tabs[1]
   import {slide,scale} from 'svelte/transition'
   let data ;
   import New from './lib/New.svelte';
import {onMount} from 'svelte'
     import {app,db} from './lib/config.svelte';
    import { addDoc,collection,onSnapshot,deleteDoc ,doc } from "https://www.gstatic.com/firebasejs/9.6.10/firebase-firestore.js";
   onMount(() => {
const q = collection(db, "blogs") 
const unsubscribe = onSnapshot(q, (querySnapshot) => {
data = querySnapshot.docs
  // console.log("Current cities in CA: ", cities.join(", "));
});
   })
   const deleteDocFun = async e=>{
    await deleteDoc(doc(db,'blogs',e.target.id))
   }
</script>

<main>

  <nav class="purple darken-2">
    <div class="nav-wrapper container">
      <a href="#" class="brand-logo">Blog</a>
      <ul id="nav-mobile" class="right hide-on-sm-and-down">
        <li><a href="#"  on:click={() => currentTabs ='Make New Guide'}>New Blog</a></li>
        <li><a href="#" on:click={( ) => currentTabs ='Home'} >Home</a></li>
        <li><a href="#">View Details</a></li>
      </ul>
    </div>
  </nav>
<div class="container row" >
        
{#if currentTabs == 'Make New Guide'}
<div in:slide out:scale>

<New  />
</div>
{:else if currentTabs == 'Home'}
{#if data}
{#each data as item}
<div class="col s12 m6" >
  <div class="card blue-grey darken-1 " in:slide out:scale>
    <div class="card-content text-white">
      <span class="card-title text-white">{item.data().title}</span>
    <p>
      {item.data().body}

    </p>

    </div>
    <div class="card-action">
      <button class="red btn" id={item.id} on:click="{deleteDocFun}">
        Delete
      </button>
    </div>
  </div>
</div>
{/each}
{/if}

{/if}
</div>

</main>

<style>
.card{
  color: #fff;
}
</style>
