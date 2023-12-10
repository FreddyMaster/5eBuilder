<script>
    import { NativeSelect } from '@svelteuidev/core'; // Importing the Select component from the Mantine library
    import backgrounds from './data/backgrounds.json'; // Importing background data from a JSON file
    import alignments from './data/alignments.json'; // Importing alignment data from a JSON file
  
    let selectedAlignment = null; // Defining state to keep track of selected alignment
    let selectedBackground = null; // Defining state to keep track of selected background
    
    // A function to update the state when an alignment is selected from the dropdown
    function handleAlignmentChange(event) {
      selectedAlignment = event;
    }
  
    // A function to update the state when a background is selected from the dropdown
    function handleBackgroundChange(event) {
      selectedBackground = event;
    }
  </script>
  
  <div id="Background" class="tabcontent">
    <h2>Background / Alignment</h2>
    <!-- Rendering the Select component with alignment data -->
    <label for="alignment-dropdown">Select an Alignment</label>
    <div id="alignment-dropdown">
    <NativeSelect
      id="alignment-dropdown"
      data={alignments.map((alignment) => alignment.name)}
      description="Select 1"
      placeholder="Select an alignment"
      bind:value={selectedAlignment}   
    />
    </div>
    <!-- Rendering the Select component with background data -->
    <label for="background-dropdown">Select a Background</label>
    <div id="background-dropdown">
    <NativeSelect
      id="background-dropdown"
      data={backgrounds.map((background) => background.name)}
      description="Select 1"
      placeholder="Select a background"
      bind:value={selectedBackground}
    />
    </div>
  </div>

  <style>
    label {
        font-size: 1.17em;
        font-weight: bold;
        margin-bottom: 5px;
    }
    #alignment-dropdown {
        margin-bottom: 20px;
        width: 200px;
    }
    #background-dropdown {
        margin-bottom: 20px;
        width: 200px;
    }
  </style>
  