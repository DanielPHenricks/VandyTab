<script>
    import games from "../games.json";
    import ButtonModal from "./ButtonModal.svelte";
    const time = new Date();
    const date = time.getDate();
    const month = time.getMonth() + 1;
    const hours = time.getHours();
    const monthToDigit = {
        "Jan ": 1,
        "Feb ": 2,
        "Mar ": 3,
        "Apr ": 4,
        "May ": 5,
    };

    const sportsTypes = [
        "Men's Basketball",
        "Baseball",
        "Swimming",
        "Women's Basketball",
        "Men's Tennis",
        "Women's Tennis",
    ];

    const compareTimes = (/** @type {string} */ a, /** @type {string} */ b) => {
        let aTime = a.indexOf("PM") ? 12 : 0;
        let bTime = b.indexOf("PM") ? 12 : 0;
        aTime += parseInt(a.substring(0, a.indexOf(":")));
        bTime += parseInt(b.substring(0, b.indexOf(":")));
        return aTime % 12 <= bTime % 12 ? -1 : 1;
    };

    games.sort((a, b) => {
        const firstDate =
            "" +
            monthToDigit[a.date.substr(0, 4)] +
            a.date.substr(4, a.date.length - 4).padStart(2, "0");
        const secondDate =
            "" +
            monthToDigit[b.date.substr(0, 4)] +
            b.date.substr(4, b.date.length - 4).padStart(2, "0");
        return firstDate == secondDate
            ? compareTimes(a.time, b.time)
            : firstDate > secondDate
            ? 1
            : -1;
    });

    const prefs = localStorage.getItem("prefs");
    const parsed = prefs != undefined ? JSON.parse(prefs) : undefined;
    // the filter method does not change the original json
    let filteredGames = games.filter((game) => {
        if (parsed != undefined) {
            return !(
                monthToDigit[game.date.substr(0, 4)] < month ||
                (monthToDigit[game.date.substr(0, 4)] == month &&
                    parseInt(game.date.substring(4, game.date.length)) <
                        date) ||
                parsed.indexOf(game.sport) == -1
            );
        }
        return !(
            monthToDigit[game.date.substr(0, 4)] < month ||
            (monthToDigit[game.date.substr(0, 4)] == month &&
                parseInt(game.date.substring(4, game.date.length)) < date)
        );
    });
</script>

<table id="rounded-corner" summary="Dining">
    <thead>
        <tr>
            <th scope="col" class="rounded-company" />
            <th scope="col" class="rounded-q1">
                <img
                    src="../images/sports.png"
                    height="20"
                    width="20"
                    alt="Sports"
                /> Sports
            </th>
            <th scope="col" class="rounded-q1">
                <ButtonModal buttonTopics={sportsTypes} />
            </th>
        </tr>
    </thead>

    <tbody id="table">
        <tr>
            <td><b>Date</b></td>
            <td><b>Time</b></td>
            <td><b>Opponent</b></td>
        </tr>
        {#each filteredGames as game}
            <tr>
                <td>{game.date}</td>
                <td>{game.time}</td>
                <td
                    >{game.sport}
                    {game.isHomeGame ? "vs" : "at"}
                    {game.opponent}</td
                >
            </tr>
        {/each}
    </tbody>
</table>

<style type="text/css">
    tbody td:first-child {
        width: 60px;
    }
    tbody td:nth-child(2) {
        width: 70px;
    }
    ::-webkit-scrollbar {
        width: 10px;
        height: 3px;
    }
    ::-webkit-scrollbar-button {
        width: 0px;
        height: 0px;
    }
    ::-webkit-scrollbar-thumb {
        background: #ffffff;
        border: 0px none #ffffff;
        border-radius: 0px;
    }
    ::-webkit-scrollbar-thumb:active {
        background: #ffffff;
    }
</style>
