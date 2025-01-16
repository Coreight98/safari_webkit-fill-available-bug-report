<script lang="ts">
  
  const scrollIntoViewTop = () => {
    const top = document.getElementById('0');
    top.scrollIntoView({ behavior: 'smooth' });
  };

  const scrollIntoViewBottom = () => {
    const bottom = document.getElementById('99');
    bottom.scrollIntoView({ behavior: 'smooth' });
  };

  const scrollToTop = () => {
    window.scrollTo({ top: 0, behavior: 'smooth' });
  };

  const scrollToBottom = ()=>{
    window.scrollTo({ top: document.body.scrollHeight, behavior: 'smooth' });
  }
</script>

<main>
  <div class='doc-main'>
  {#each Array.from({length: 100}, (_, i) => i) as i}
    <div class="block" id={String(i)}>
      {i}
    </div>
  {/each}
  </div>
  <div class="navi">
    <button class="top" on:click={scrollIntoViewTop}>scrollIntoView top</button>
    <button class="bottom" on:click={scrollIntoViewBottom}>scrollIntoView bottom</button>
    <button class="top" on:click={scrollToTop}>scrollTo top</button>
    <button class="bottom" on:click={scrollToBottom}>scrollTo bottom</button>
  </div>
</main>

<style>
  main {
    display: block;
    width: 100%;
    height: 100%;
  }
  .navi {
    position: fixed;
    bottom: 0;
    right: 0;
    display: flex;
    flex-direction: column;
    gap: 2px;
  }
  .block {
    width: 100%;
    height: 100px;
    border: 1px solid black;
    box-sizing: border-box;
  }
@supports (-webkit-touch-callout: none){
  .doc-main{
      height:-webkit-fill-available;
      overflow:hidden;
      overflow-y:auto;
  }

}
</style>
