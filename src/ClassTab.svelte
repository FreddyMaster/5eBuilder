<!-- ClassLevelDropdowns.svelte -->
<script>
    import { NativeSelect } from "@svelteuidev/core";
    import classes from "./data/classes.json"; // Import classes data from a JSON file

    // Define a variable to hold the selected class and initialize it to null
    let selectedClass = null;
    // Declare hitDie variable
    let hitDie = null;

    // Define an array to hold level options from 1 to 20
    const levelOptions = Array.from({ length: 20 }, (_, i) => ({
        value: i + 1,
        label: `Level ${i + 1}`,
    }));

    // Define a variable to hold the selected level and initialize it to null
    let selectedLevel = null;

    // Function to handle class selection
    function handleClassChange(event) {
        selectedClass = event.target.value;
    }

    // Function to handle level selection
    function handleLevelChange(event) {
        selectedLevel = parseInt(event.target.value, 10);
    }

    // Define a reactive statement to compute the hit die based on the selected class
    $: {
        if (selectedClass) {
            const selectedClassData = classes.find(
                (classItem) => classItem.name === selectedClass
            );
            if (selectedClassData) {
                hitDie = selectedClassData.hit_die;
            } else {
                hitDie = null;
            }
        } else {
            hitDie = null;
        }
    }
</script>

<div>
    <h2>Select a Class and Level</h2>
    <label for="class-dropdown">Select a Class</label>
    <div id="class-dropdown">
        <!-- Dropdown for selecting a class from JSON data -->
        <NativeSelect
            data={classes.map((item) => item.name)}
            id="class-dropdown"
            on:change={handleClassChange}
            placeholder="Select a Class"
            description="Select 1"
            required={false}
        />
    </div>
    <label for="level-dropdown">Select Your Character's Level</label>
    <div id="level-dropdown">
        <!-- Dropdown for selecting a level from 1 to 20 -->
        <NativeSelect
            data={levelOptions}
            id="level-dropdown"
            on:change={handleLevelChange}
            placeholder="Select a Level"
            description="Select 1"
            required={false}
        />
    </div>
    <p>
        {#if hitDie !== null}
            {selectedClass}(d{hitDie})
            <br />
        {/if}
        Level: {selectedLevel || "None"}
    </p>
</div>

<style>
    label {
        font-size: 1.17em;
        font-weight: bold;
        margin-bottom: 5px;
    }
    #class-dropdown {
        margin-bottom: 20px;
        width: 200px;
    }
    #level-dropdown {
        margin-bottom: 20px;
        width: 200px;
    }
</style>
