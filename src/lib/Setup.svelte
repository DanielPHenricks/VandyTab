<script>
    const setName = () => {
        let name = document.getElementById("nameInput").value;
        localStorage.name = name;
    };
</script>

<html lang="en">
    <body>
        <div id="container">
            <p>Welcome to VandyTab!</p>
            <div id="greeting">
                <div style="max-height: 1vh">
                    <input type="text" id="nameInput" />
                    <button id="submitButton" on:click={() => setName()}
                        >Save name</button
                    >
                </div>
            </div>
        </div>
    </body>
</html>

<style>
    /* This is the style for the greeting */
    #container {
        background-color: transparent;
        text-align: center;
        position: relative;
        top: 0em;
        text-shadow: 0 2px 3px rgba(0, 0, 0, 0.9);
    }
    #greeting {
        font: 20pt Roboto, Century Gothic;
        color: #fbf9f9;
        text-shadow: 0 0 10px rgba(0, 0, 0, 1);
    }
</style>
