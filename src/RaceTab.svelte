<script>
    // @ts-nocheck

    import { TextInput, Button, Tooltip, rem } from "@svelteuidev/core";
    import races from "./data/races.json";

    let selectedRace = null;
    let name = "";
    let description = null;

    const items = races.map((race) => ({
        id: race.name,
        label: `Size: ${race.size}, speed: +${
            race.speed
        }, languages: ${race.languages.join(", ")}`,
        color: "dark",
        withArrow: true,
    }));

    function handleButtonClick(event, race) {
        selectedRace = race.id;
        if (event.type === "mouseenter") {
            description = race.label;
        } else {
            description = null;
        }
    }

    const buttonStyles = (raceId) => {
        return {
            border: `${rem(1)} solid transparent`,
            margin: `${rem(5)}`,
            zIndex: 0,
            width: "150px",
            boxSizing: "border-box",
            '&:hover': {
                transition: "100ms",
                border: `${rem(2)} solid #3ca9cd`,
            },
            backgroundColor: selectedRace === raceId ? "#3ca9cd" : "#1A1B1E",
        };
    };
</script>

<div id="Race" class="tabcontent">
    <h2>Race</h2>
    <div id="name">
        <TextInput
            id="name"
            class="name"
            placeholder="Your Name"
            label="Name"
            bind:value={name}
        />
    </div>
    <h3 id="race">Race</h3>
    <em id="select1">Select 1</em>
    <div class="container">
        {#each items as item (item.id)}
            <div>
                <Tooltip
                    transitionDuration={200}
                    width={250}
                    label={item.label}
                    wrapLines
                    color="dark"
                    withArrow
                    on:mouseenter={() => handleButtonClick(event, item)}
                    on:mouseleave={() => handleButtonClick(event, item)}
                >
                    <Button
                        color="#1A1B1E"
                        override={buttonStyles(item.id)}
                        on:click={() => (selectedRace = item.id)}
                    >
                        {item.id}
                    </Button>
                </Tooltip>
            </div>
        {/each}
    </div>
</div>

<style>
    #name {
        width: 200px;
    }
    .container {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
    }
</style>
