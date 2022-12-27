# Todo-List-app
First create file naming index.html then copy paste the code given below

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Todo app | By Deepak Pathak</title>
    <link rel="stylesheet" href="style.css">
</head>

<body>
    <main>
        
        <div class="box">
            <h1 style="color: #3498db; text-align: center; padding: 10px;"   >Todo...</h1>
            <input type="text" id="item" autofocus placeholder="Create your todo list...">
            <ul id="to-do-box">
            </ul>
        </div>
    </main>
    <script src="https://kit.fontawesome.com/bf520e6492.js" crossorigin="anonymous"></script>
    <script src="script.js"></script>
</body>

</html>

# create style.css then copy paste the code given below

@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@300&display=swap');
* {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    font-family: 'Open Sans', sans-serif;
}

main {
    width: 100%;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color:#3498db;
}

.box {

    width: 700px;
    min-height: 500px;
    max-height: 500;
    background-color: rgb(250, 246, 246);
    border-radius: 5px;
    padding: 15px;
    overflow-y: auto;
}

#item {
    padding: 20px;
    max-height: fit-content;
    font-size: 20px;
    width: 100%;
    border: 20px;
    outline: 10;
    display: block;
    font-weight: bold;
    overflow-y: auto;
    box-shadow: 1px 2px 2px #3498db;
}

#to-do-box {
    margin-right: 20px;
    list-style: none;
    overflow-y: auto;
}

#to-do-box li {
    position: relative;
    background-color: #3498dbc3;
    max-height: 600px;
    overflow-y: auto;
    color: rgb(255, 255, 255);
    padding: 10px;
    border-radius: 10px;
    padding-right: 30px;
    text-align: justify;
    margin-top: 10px;
    user-select: none;
}

#to-do-box li i {
    position: absolute;
    right: 10px;
    top: 10px;
}

.done {
    text-decoration: line-through;
    color: black;
    background-color: #95a5a6 !important;
}

# then again create a file naming script.js and copy paste the code

const item = document.querySelector("#item")
const toDoBox = document.querySelector("#to-do-box")

item.addEventListener(
    "keyup",
    function(event) {
        if (event.key == "Enter") {
            addToDo(this.value)
            this.value = ""
        }
    }
)

const addToDo = (item) => {
    const listItem = document.createElement("li");
    listItem.innerHTML = `
         ${item}
        <i class="fas fa-times"></i>
    `;

    listItem.addEventListener(
        "click",
        function() {
            this.classList.toggle("done");
        }
    )
    listItem.querySelector("i").addEventListener(
        "click",
        function() {
            listItem.remove()
        }
    )
    toDoBox.appendChild(listItem)
}
