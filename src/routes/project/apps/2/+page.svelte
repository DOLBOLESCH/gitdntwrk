<h1>Expense-list</h1>
<form>
    <!-- svelte-ignore a11y-label-has-associated-control -->
    <label>Название:</label>
    <input bind:value={newName} type="text" placeholder="Хлеб">
    <!-- svelte-ignore a11y-label-has-associated-control -->
    <label>Цена:</label>
    <input bind:value={newAmount} type="text" placeholder="50">
    <button on:click={addExpense}><span>Добавить</span></button>
  </form>
<table>
    <thead>
    <tr>
        <th>Название</th>
        <th>Cумма</th>
        <th>Действия</th>
    </tr>
    </thead>

    <tbody>
    {#each expenses as expense, i}
    <tr>
        <td><div>{expense.name}</div></td>
        <td><div>{expense.amount}</div></td>
        <td><button on:click={() => deleteExpense(i)}>Убрать</button></td>
    </tr>
    {/each}
    </tbody>
</table>

<script>
    let expenses = [];

    let newName = '';
    let newAmount = '';

    function addExpense() {
        const obj = {
            name: newName,
            amount: parseInt(newAmount),
        };
        expenses.push(obj);
        expenses = expenses;
        newName = '';
        newAmount = '';
    }

    function deleteExpense(index) {
        expenses.splice(index, 1);
        expenses = expenses;
    }
</script>

<style>
    label {
        display: block;
        margin-bottom: 10px;
    }

    input[type='text'] {
        padding: 5px;
        border:1px solid #ccc;
        border-radius: 5px;
        margin-right: 10px;
        width: 150px;
    }
    
    table {
        margin-top: 20px;
        border-collapse: collapse;
        width: 100%;
        font-family: "Lucida Sans Unicode", "Lucida Grande", Sans-Serif;
        font-size: 14px;
        text-align: left;
        border-radius: 20px;
        box-shadow: 0 0 0 10px #F2906B;
        color: #452F21;
}

    th,
    td {
        border: 1px solid #ccc;
        padding: 8px;
        text-align: left;
        border-top: 10px solid #F2906B;
    background: white;
    }
    
    th {
        background-color: white;
        padding: 10px 8px;
    }

    button {
        padding: 5px 10px;
        background-color: #4caf50;
        color: white;
        border: none;
        border-radius: 5px;
        cursor: pointer;
    }
    h1 {
        font-size: 24px;
        margin-bottom:20px;
    }

    table th:first-child {
        border-top-left-radius: 20px;
    }
    table th:last-child {
        border-top-right-radius: 20px;
    }
    table td:first-child {
        border-bottom-left-radius: 20px;
    }
    table td:last-child {
        border-bottom-right-radius: 20px;
    }
</style>