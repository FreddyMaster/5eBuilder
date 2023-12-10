<!-- FeatTab.svelte -->
<script>
// @ts-nocheck

    import { Tooltip, Button, createStyles, rem } from '@svelteuidev/core';
    import feats from "./data/feats.json";
  
    let selectedFeat = null;
    let description = null;
  
    // Map through feats array and create Tooltip and Button components for each feat
    let items = feats.map((feat) => ({
      name: feat.name,
      benefit: feat.benefit,
    }));
  
    // Function to handle button click and mouse events
    function handleButtonClick(event, feat) {
      selectedFeat = feat.name;
  
      // Handle mouse enter and leave events
      if (event.type === "mouseenter") {
        description = `Benefits: ${feat.benefit}`;
      } else {
        description = null;
      }
    }
    
    const buttonStyles = (featId) => {
        return {
            border: `${rem(1)} solid transparent`,
            margin: `${rem(5)}`,
            zIndex: 0,
            width: "200px",
            boxSizing: "border-box",
            '&:hover': {
                transition: "100ms",
                border: `${rem(2)} solid #3ca9cd`,
            },
            backgroundColor: selectedFeat === featId ? "#3ca9cd" : "#1A1B1E",
        };
    };
  </script>
  
<div id="Feat" class="tabcontent">
  <h2>Feats</h2>
  <div class="Feats">
    {#each items as feat (feat.name)}
      <Tooltip
        class="feat-tooltip"
        transitionDuration={300}
        width={400}
        wrapLines
        label={`Benefits: ${feat.benefit}`}
        color="dark"
        withArrow
      >
        <Button
          class="feat-button"
          color="#1A1B1E"
          override={buttonStyles(feat.id)}
          on:click={() => selectedFeat = feat.name}
          on:mouseenter={(event) => handleButtonClick(event, feat)}
          on:mouseleave={(event) => handleButtonClick(event, feat)}
        >
          {feat.name}
        </Button>
      </Tooltip>
    {/each}
  </div>
</div>

<style>
  .Feats {
      display: flex;
      flex-direction: column;
      align-items: flex-start;
  }
</style>
