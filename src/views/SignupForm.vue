<template>
    <form action="">
        <label for="emailinput">Email</label>
        <input type="email" required id="emailinput" v-model="stringEmail" />

        <label for="passwordinput">Password</label>
        <input type="password" required v-model="stringPassword" id="passwordinput" />
    </form>

    <p>Email : {{ stringEmail }}</p>
    <p>Password : {{ stringPassword }}</p>
</template>

<script>
export default {
    name: 'SignupFormComponent',
    setup() {
        return {};
    },
    data() {
        return {
            stringEmail: '',
            stringPassword: '',
        };
    },
    methods: {
        sendEmail() {
            // send email
        },
    },
};
</script>

<style lang="scss">
form {
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
}
label {
    color: #aaa;
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
