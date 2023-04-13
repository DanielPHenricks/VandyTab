<script>
    import dininghalls from "../dininghalls.json";
    import FoodModal from "./FoodModal.svelte";
    const date = new Date();
    const day = date.getDay();
    const hour = date.getHours();
    const isOpen = (
        /** @type {{ name?: string; openHour: any; closedHour: any; }} */ hall
    ) => {
        let open = false;
        open = hour >= hall.openHour[day] && hour < hall.closedHour[day];
        return open ? `../images/open.png` : `../images/closed.png`;
    };
    const diningHallNames = [
        "The Commons",
        "Rothschild",
        "EBI",
        "Rand",
        "Zeppos",
        "Kissam",
    ];

    const prefs = localStorage.getItem("foodPrefs");
    console.log(prefs);
    const parsed = prefs == undefined ? undefined : JSON.parse(prefs);
    let filteredDiningHalls =
        parsed == undefined
            ? dininghalls
            : dininghalls.filter((dininghall) => {
                  return parsed.includes(dininghall.name);
              });
</script>

<!-- This component is for the table containing upcoming schedules. -->
<table id="rounded-corner" summary="Dining">
    <thead>
        <tr>
            <th scope="col" class="rounded-company" />
            <th scope="col" class="rounded-q1">
                <img
                    src="../images/food.png"
                    height="20"
                    width="20"
                    alt="Food"
                /> Food
            </th>
            <th scope="col" class="rounded-q1">
                <FoodModal buttonTopics={diningHallNames} />
            </th>
        </tr>
    </thead>

    <tbody id="table">
        {#each filteredDiningHalls as hall}
            <tr>
                <td><img id="open1" src={isOpen(hall)} alt="img" /></td>
                <td>{hall.name}</td>
                <td />
            </tr>
        {/each}
    </tbody>
</table>

<style type="text/css">
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

    tbody td:first-child {
        width: 0px;
    }

    tbody td:nth-child(2) {
        width: 200px;
    }

    tbody td:nth-child(3) {
        width: 160px;
    }

    thead th:first-child {
        border-top-left-radius: 10px;
    }

    thead th:nth-child(3) {
        border-top-right-radius: 10px;
    }
</style>
