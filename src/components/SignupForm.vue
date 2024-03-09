<template>
    <form>
        <label for="email">Email</label>
        <input type="email" name="email" id="email" required>
    </form>
</template>
<script>
export default {

}
</script>
<style>

form {
    max-width: 420px;
    margin: 30px auto;
    background-color: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
}

label {
    color: #AAAAAA;
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
    border-bottom: 1px solid #DDDDDD;
    color: #555555;
}
</style>