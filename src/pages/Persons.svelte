<script>

    import axios from "axios";
    import { onMount } from "svelte";

    let persons = [];

    onMount( () => {
        getPersons();
    })

    function getPersons() {
        axios.get("http://localhost:8080/infections/persons")
            .then(response => {
                persons = response.data;
        })
    }

    function postPersons() {
        axios.post("http://localhost:8080/infections/persons")
            .then()
    }

</script>

<h1>List of all persons</h1>

<table class="table">
    <thead>
        <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Birthdate</th>
        </tr>
    </thead>
    <tbody>
        {#each persons as person}
        <tr>
            <td>{person.id}</td>
            <td>{person.name}</td>
            <td>{person.birthdate}</td>
        </tr>
        {/each}
    </tbody>
</table>