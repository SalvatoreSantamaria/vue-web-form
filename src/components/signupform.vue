<template>
    <div>
        <form>
            <label>Email: </label> 
            <!-- Two way data binding one: v-model= will connect and update to the data property email -->
            <input type="email" required v-model="email">

            <label>Password: </label>
            <input type="password" required v-model="password">

        </form>
        <p>Email: {{ email }}</p>
        <p>Password: {{ password }}</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            email: '', // Two way data binding two: data is updated by the v-model
            password: ''
        }
    }
}
</script>

<style>
    form {
        max-width: 420px;
        margin: 30px auto;
        background: white;
        text-align: left;
        padding: 40px;
        border-radius: 10px;
    }
    label {
        color: aaa;
        display: inline-block;
        margin: 25px 0 15px;
        font-size: 0.6em;
        text-transform: uppercase;
        letter-spacing: 1px;
        font-weight: bold;
    }
    input {
        display: block;
        padding: 10px 6px;
        width: 100%;
        box-sizing: border-box;
        border: none;
        border-bottom: 1px solid #ddd;
        color: #555;
    }
</style>