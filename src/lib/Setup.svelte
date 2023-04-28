<!-- 
    This component contains the declaration for the setup of prefs for the extension. 
    Last changed: 4/28/23
-->

<script>
    const diningHallNames = [
        "The Commons",
        "Rothschild",
        "EBI",
        "Rand",
        "Zeppos",
        "Kissam",
    ];
    const sportsTypes = [
        "Men's Basketball",
        "Baseball",
        "Swimming",
        "Women's Basketball",
        "Men's Tennis",
        "Women's Tennis",
    ];
    const setName = () => {
        // @ts-ignore
        let name = document.getElementById("nameInput").value;
        localStorage.name = name;
        getCheckedBoxes();
        location.reload(); // This will reload the document and save the preference.
    };

    const getCheckedBoxes = () => {
        const form = document.querySelector("#buttonForm");
        let checked = form.querySelectorAll('input[type="checkbox"]:checked');
        let labels = [];
        checked.forEach((box) => {
            const label = form.querySelector('label[for="' + box.id + '"]');
            labels.push(label.innerHTML);
        });
        let string = JSON.stringify(labels);
        localStorage.setItem("foodPrefs", string);

        const sports = document.querySelector("#sportsButtonForm");
        checked = sports.querySelectorAll('input[type="checkbox"]:checked');
        labels = [];
        checked.forEach((box) => {
            const label = sports.querySelector('label[for="' + box.id + '"]');
            labels.push(label.innerHTML);
        });
        string = JSON.stringify(labels);
        localStorage.setItem("prefs", string);
    };
</script>

<!-- Note that you do not need to include a html or body element here since the parent has it -->
<div id="container">
    <h4 id="black-text">Welcome to VandyTab! Please enter your name below.</h4>
    <div id="greeting">
        <div style="max-height: 1vh">
            <input type="text" id="nameInput" />
            <div class="row d-flex justify-content-between">
                <div class="col-md-4" />
                <div class="col-md-4">
                    <div id="align-left">
                        <h4 id="black-text">
                            Select your preferred dining halls:
                        </h4>
                        <form id="buttonForm">
                            <div class="text-left">
                                {#each diningHallNames as topic}
                                    <input
                                        class="form-check-input mt-2"
                                        type="checkbox"
                                        value=""
                                        id="defaultCheck{topic}"
                                    />
                                    <label
                                        class="form-check-label"
                                        id="black-text"
                                        for="defaultCheck{topic}"
                                        >{topic}
                                    </label>
                                    <br />
                                {/each}
                            </div>
                        </form>
                        <h4 id="black-text">
                            Select sports you want to follow:
                        </h4>
                        <form id="sportsButtonForm">
                            <div class="text-left">
                                {#each sportsTypes as topic}
                                    <input
                                        class="form-check-input mt-2"
                                        type="checkbox"
                                        value=""
                                        id="sportsDefaultCheck{topic}"
                                    />
                                    <label
                                        class="form-check-label"
                                        id="black-text"
                                        for="sportsDefaultCheck{topic}"
                                        >{topic}
                                    </label>
                                    <br />
                                {/each}
                            </div>
                        </form>
                    </div>
                </div>
                <div class="col-md-4" />
            </div>

            <button id="submitButton" on:click={() => setName()}>Save</button>
        </div>
    </div>
</div>

<style>
    #container {
        background-color: transparent;
        text-align: center;
        position: relative;
        text-shadow: 0 2px 3px rgba(0, 0, 0, 0.9);
        color: white;
    }
    #greeting {
        font: 20pt Roboto, Century Gothic;
        color: #fbf9f9;
        text-shadow: 0 0 10px rgba(0, 0, 0, 1);
    }
    #align-left {
        margin: 5px;
        font: 12pt Roboto, Century Gothic;
        text-align: left;
        position: relative;
        text-shadow: 0 2px 3px rgba(0, 0, 0, 0.9);
    }
    #black-text {
        color: black;
        text-shadow: 2px 2px 3px rgba(255, 255, 255, 0.9);
    }
</style>
