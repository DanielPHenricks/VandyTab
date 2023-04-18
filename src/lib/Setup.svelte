<!-- 
    This component contains the declaration for the setup of prefs for the extension. 
    Last changed: 4/17/23
-->

<script>
    const setName = () => {
        let name = document.getElementById("nameInput").value;
        localStorage.name = name;
        location.reload(); // This will reload the document and save the preference.
    };
</script>

<!-- Note that you do not need to include a html or body element here since the parent has it -->
<div id="container">
    <h4>Welcome to VandyTab! Please enter your name below.</h4>
    <div id="greeting">
        <div style="max-height: 1vh">
            <input type="text" id="nameInput" />
            <button id="submitButton" on:click={() => setName()}
                >Save name</button
            >
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
</style>
