<script>
    import "bootstrap-icons/font/bootstrap-icons.css";

    // Whether the modal should be shown or not.
    let showModal = false;

    // What the default button title should be.
    const buttonTitle = "Edit";

    // The title for the modal.
    export let modalTitle = "Set Preferences";

    // The text in the middle of the modal.
    export let buttonTopics = [];

    // By default, there are no prefs.
    let hasSavedPrefs = localStorage.getItem("prefs") != undefined;

    // The saved preferences.
    export let savedPrefs = hasSavedPrefs
        ? JSON.parse(localStorage.getItem("prefs"))
        : [];

    // When the submit button is clicked, process the data.
    const processButtonClick = () => {
        const form = document.querySelector("#buttonForm");
        const checked = form.querySelectorAll('input[type="checkbox"]:checked');
        let labels = [];
        checked.forEach((box) => {
            const label = form.querySelector('label[for="' + box.id + '"]');
            labels.push(label.innerHTML);
        });
        const string = JSON.stringify(labels);
        localStorage.setItem("prefs", string);
    };

    // Load the saved prefs and prepare the modal.
    const loadModal = () => {
        showModal = true;
        modalTitle = (hasSavedPrefs ? "Saved" : "Set") + " Preferences";
    };

    // Are the topics the default ones or have they been updated?
    const getTopics = () => {
        return hasSavedPrefs ? savedPrefs : buttonTopics;
    };

    // Set the prefs variable back to default.
    const resetPrefs = () => {
        savedPrefs = [];
        hasSavedPrefs = false;
        localStorage.removeItem("prefs");
    };
</script>

<button on:click={() => loadModal()}
    ><i class="bi bi-pencil" />{buttonTitle}</button
>

{#if showModal}
    <div class="modal-overlay">
        <div class="modal-content dark-mode">
            <h3>{modalTitle}</h3>
            <form id="buttonForm">
                <div class="text-left">
                    {#each getTopics() as topic}
                        <input
                            class="form-check-input mt-2"
                            type="checkbox"
                            value=""
                            id="defaultCheck{topic}"
                        />
                        <label
                            class="form-check-label"
                            for="defaultCheck{topic}"
                        >
                            {topic}
                        </label>
                        <br />
                    {/each}
                </div>
                <button
                    type="submit"
                    class="btn btn-primary m-3"
                    on:click={() => processButtonClick()}>Submit</button
                >
                <button
                    class="btn btn-primary m-3"
                    on:click={() => resetPrefs()}>Reset</button
                >
            </form>
            <button
                on:click={() => {
                    showModal = false;
                }}>Close</button
            >
        </div>
    </div>
{/if}

<style>
    .modal-overlay {
        position: fixed;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        background-color: rgba(0, 0, 0, 0.5);
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .modal-content {
        max-width: 30vw;
        padding: 1rem;
        border-radius: 4px;
        justify-content: center;
    }

    .dark-mode {
        background-color: black;
        color: white;
    }

    .text-left {
        text-align: left;
    }

    label {
        display: inline-block;
    }
    i {
        margin-right: 2px;
    }
</style>
