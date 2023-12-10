<!-- Your main component -->
<script>
	import { Tabs, SvelteUIProvider } from "@svelteuidev/core";
	import Icon from "@iconify/svelte";
	import races from "./data/races.json";

	// Import the tab components
	import RaceTab from "./RaceTab.svelte";
	import ClassTab from "./ClassTab.svelte";
	import AbilityScoresTab from "./AbilityScoresTab.svelte";
	import BackgroundTab from "./BackgroundTab.svelte";
	import FeatsTab from "./FeatsTab.svelte";
	import ProficienciesTab from "./ProficienciesTab.svelte";

  // Define your abilityScores data as an array of objects
  let abilityScores = [
    { name: 'Strength', score: 10, modifier: '0' },
    { name: 'Dexterity', score: 10, modifier: '0' },
    { name: 'Constitution', score: 10, modifier: '0' },
    { name: 'Intelligence', score: 10, modifier: '0' },
    { name: 'Wisdom', score: 10, modifier: '0' },
    { name: 'Charisma', score: 10, modifier: '0' },
  ];

  // Function to update abilityScores
  function setAbilityScores(newAbilityScores) {
    abilityScores = newAbilityScores;
  }
</script>
<SvelteUIProvider hemeObserver={'dark'}>
<Tabs variant="pills" tabPadding="md">
	<Tabs.Tab label="Race">
		<!-- Use the RaceTab component here -->
		<RaceTab />
	</Tabs.Tab>
	<Tabs.Tab label="Class / Level">
		<!-- Use the ClassTab component here -->
		<ClassTab />
	</Tabs.Tab>
	<Tabs.Tab label="Ability Scores / Feats">
		<!-- Use the AbilityScoresTab component here and pass the required props -->
		<AbilityScoresTab/>
	</Tabs.Tab>

	<Tabs.Tab label="Background">
		<!-- Use the BackgroundTab component here -->
		<BackgroundTab />
	</Tabs.Tab>
	<Tabs.Tab label="Feats">
		<!-- Use the ProficienciesTab component here -->
		<FeatsTab />
	</Tabs.Tab>
	<Tabs.Tab label="Proficiencies">
		<!-- Use the ProficienciesTab component here -->
		<ProficienciesTab />
	</Tabs.Tab>
</Tabs>
</SvelteUIProvider>