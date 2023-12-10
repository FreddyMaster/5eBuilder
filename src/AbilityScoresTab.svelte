<!-- AbilityScores.svelte -->
<script>
  import { NumberInput } from '@svelteuidev/core';
  // Define the state variables for ability scores and modifiers
  let strength = 10;
  let dexterity = 10;
  let intelligence = 10;
  let wisdom = 10;
  let charisma = 10;

  // Function to calculate the modifier for a given ability score
  function calculateModifier(score) {
    const modifier = Math.floor((score - 10) / 2);
    return modifier >= 0 ? `+${modifier}` : modifier;
  }

  // Update modifiers when ability scores change
  $: strengthModifier = calculateModifier(strength);
  $: dexterityModifier = calculateModifier(dexterity);
  $: intelligenceModifier = calculateModifier(intelligence);
  $: wisdomModifier = calculateModifier(wisdom);
  $: charismaModifier = calculateModifier(charisma);
</script>

<style>
  .ability-score-container {
      display: flex;
      align-items: center;
      margin-bottom: 10px;
  }

  .ability-label {
      font-weight: bold;
      width: 100px;
  }
  .modifier {
    padding-left: 10px;
    font-weight: bold;
  }
</style>

<div>
  <h2>Ability Scores</h2>
  <div class="ability-score-container">
      <label class="ability-label" for="strength">Strength:</label>
      <NumberInput id="strength" bind:value={strength} min={1} max={30} />
      <span class="modifier">{strengthModifier}</span>
  </div>
  <div class="ability-score-container">
      <label class="ability-label" for="dexterity">Dexterity:</label>
      <NumberInput id="dexterity" bind:value={dexterity} min={1} max={30} />
      <span class="modifier">{dexterityModifier}</span>
  </div>
  <div class="ability-score-container">
      <label class="ability-label" for="intelligence">Intelligence:</label>
      <NumberInput id="intelligence" bind:value={intelligence} min={1} max={30} />
      <span class="modifier">{intelligenceModifier}</span>
  </div>
  <div class="ability-score-container">
      <label class="ability-label" for="wisdom">Wisdom:</label>
      <NumberInput id="wisdom" bind:value={wisdom} min={1} max={30} />
      <span class="modifier">{wisdomModifier}</span>
  </div>
  <div class="ability-score-container">
      <label class="ability-label" for="charisma">Charisma:</label>
      <NumberInput id="charisma" bind:value={charisma} min={1} max={30} />
      <span class="modifier">{charismaModifier}</span>
  </div>
</div>
