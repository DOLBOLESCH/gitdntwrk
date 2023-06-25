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