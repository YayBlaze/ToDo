<title>Blaze's todo</title>

<script lang="ts">
    let task = ""
    let tasks = ["This is a meaningless task"]
    let comptasks = []
    let checktask = ""
    function addtask() {
        if (task !== ""){
            tasks.push(task)
            tasks = tasks
        }
        task = ""
    }
    function removetask() {
        comptasks.push(checktask)
        comptasks = comptasks
        let idx = tasks.indexOf(checktask)
        console.log(idx)
        tasks.splice(idx, 1)
        tasks = tasks
        checktask = ""
    }
//    if (comptasks.length == 0) {comptasks = JSON.parse(localStorage.getItem("comp")) || ""};
//    if (tasks.length == 0) {tasks = JSON.parse(localStorage.getItem("tasks")) || ""}
//
//    $: localStorage.setItem("comp",JSON.stringify(comptasks));
//    $: localStorage.setItem("tasks",JSON.stringify(tasks));
</script>


<body class="body">
    <h1 class="rainbow">Blaze's goofy ahh todo list</h1>
    <h2 class="rainbow">Add a Task:</h2>
    <h3 id="input-text">Task Name:</h3> 
    <input type="text-box" style="color: cornflowerblue;" bind:value={task}>
    <button id="update" on:click="{addtask}">Add Task</button>
    <h2 class="rainbow">Tasks todo:</h2>
    {#each tasks as task, i}
        <div class="todotask">
            <p style="color: cornflowerblue;">Task {i + 1}: {task}</p>
            <input 
                type="checkbox" 
                value={task}
                bind:group={checktask}
            />
            <p>{checktask}</p>
        </div>
    {/each}
    <button id="removetask" on:click="{removetask}">Remove all selected tasks</button>


    <h2 class="rainbow">Completed Tasks:</h2>
    {#if comptasks.length != 0}
        {#each comptasks as donetask}
            <p style="color: cornflowerblue">{donetask} is now complete! Good Job!</p>
        {/each}
    {:else}
        <p style="color: cornflowerblue;">lol no completed tasks</p>
    {/if}
</body>






<style>
    .rainbow {
        background: linear-gradient(
            45deg,
            #ff0000,
            #ff7f00,
            #ffff00,
            #00ff00,
            #0000ff,
            #4b0082,
            #8b00ff
        );
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        background-size: 400% 400%;
        -webkit-animation: rainbowanim 10s ease infinite;
        -moz-animation: rainbowanim 10s ease infinite;
        animation: rainbowanim 10s ease infinite;
    }

    @-webkit-keyframes rainbowanim {
        0% {
            background-position: 0% 50%;
        }
        50% {
            background-position: 100% 50%;
        }
        100% {
            background-position: 0% 50%;
        }
    }
    @-moz-keyframes rainbowanim {
        0% {
            background-position: 0% 50%;
        }
        50% {
            background-position: 100% 50%;
        }
        100% {
            background-position: 0% 50%;
        }
    }
    @keyframes rainbowanim {
        0% {
            background-position: 0% 50%;
        }
        50% {
            background-position: 100% 50%;
        }
        100% {
            background-position: 0% 50%;
        }
    }
    #inputtext {
        color: cornflowerblue;
    }

    #update {
        color:white;
        background-color: cornflowerblue;
        border-style: hidden;
        font-size: large;
        width: fit-content;
    }

    .body {
        background-color: black;
        width: fit-content;
    }

    .todotask {
        display: flex;
    }

    #removetask {
        color:white;
        background-color: cornflowerblue;
        border-style: hidden;
    }
</style>
