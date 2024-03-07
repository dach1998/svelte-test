<script>
    import Icon from '../../../../components/Icon.svelte';

    let newItem = '';
    let todoList = [];

    function add() {
        if (newItem !== '') {
            todoList = [
                ...todoList,
                {
                    task: newItem,
                    completed: false,
                },
            ];
            newItem = '';
        }
    }

    function remove(index) {
        todoList.splice(index, 1);
        todoList = [...todoList]; // Создаем новый массив, чтобы обновить компонент
    }

    function complete(index) {
        todoList[index].completed = !todoList[index].completed;
        todoList = [...todoList]; // Создаем новый массив, чтобы обновить компонент
    }
</script>

<main>
    <h1>My to-do list</h1>
    <form on:submit|preventDefault={add}>
        <input bind:value={newItem} placeholder="Enter to-do" />
        <button class="add-todo" on:click={add}>
            <Icon name="plus" />
        </button>
    </form>
    <div class="todos">
        {#each todoList as item, index}
            <div class="todo" class:completed={item.completed}>
                <span class="todo__text">{item.task}</span>
                <div class="todo__buttons">
                    <button class="complete" on:click={()=>complete(index)}>
                        <Icon name="check" />
                    </button>
                    <button class="delete" on:click={()=>remove(index)}>
                        <Icon name="delete" />
                    </button>
                </div>
            </div>
        {/each}
    </div>
</main>

<style>
    main {
        display: flex;
        flex-direction: column;
        align-items: center;
        min-height: 100%;
        padding: 5vmin;
        margin-top: 20px;
        box-sizing: border-box;
        background: antiquewhite;
    }

    form {
        width: 100%;
        max-width: 500px;
        display: flex;
        align-items: center;
        margin-bottom: 1rem;
    }

    input {
        flex-grow: 1;
        width: 0;
        border: none;
        border-bottom: 1px solid black;
        background: transparent;
        box-shadow: none;
        font-size: 1.2rem;
        margin: 0;
        outline: none;
    }

    .todo {
        display: flex;
        padding: 20px;
        border-radius: 20px;
        box-shadow: 0 0 15px rgb(0 0 0 / 20%);
        background-color: hsla(0, 0%, 100%, 0.2);
        margin-top: 1rem;
        font-size: 1.2rem;
        justify-content: space-between;
        align-items: center;
    }

    .todo__buttons {
        display: flex;
        align-items: center;
    }

    .todo button {
        padding: 0; /* Удаляем внутренние отступы кнопок */
        margin: 0;
        background: transparent;
        border: none;
        cursor: pointer;
    }

    .todo button:focus {
        outline: none;
    }

    .todo button .icon {
        width: 24px; /* Размер иконки */
        height: 24px;
    }

    h1 {
        text-align: center;
        font-size: 1.5rem;
        margin: 2em 0;
    }

    .delete .icon {
        color: brown;
    }

    .delete .icon:hover {
        color: darkred;
    }

    .complete .icon {
        color: cadetblue;
    }

    .complete .icon:hover {
        color: darkcyan;
    }

    .todo.completed {
        color: slategray;
    }

    .todo.completed .todo__text {
        text-decoration: line-through;
    }

    .todo.completed button {
        pointer-events: none; /* Отключаем возможность клика на кнопки в завершенных задачах */
    }

    .todos {
        width: 100%;
        max-width: 500px;
    }

    .add-todo {
        background-color: #fff;
        display: flex;
        align-items: center;
        justify-content: center;
        border: 1px solid black;
        border-radius: 6px;
        margin-left: 5px;
    }
</style>
