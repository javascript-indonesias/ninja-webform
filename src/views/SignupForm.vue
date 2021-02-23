<template>
    <form action="">
        <label for="emailinput">Email</label>
        <input type="email" required id="emailinput" v-model="stringEmail" />

        <label for="passwordinput">Password</label>
        <input type="password" required v-model="stringPassword" id="passwordinput" />

        <label for="">Role Developer</label>
        <select name="selectrole" id="selectrole" v-model="roleProfesi">
            <option value="" disabled>Select Role</option>
            <option value="webdeveloper">Web Developer</option>
            <option value="webdesigner">Web Designer</option>
            <option value="qa">Quality Assurance</option>
            <option value="systemanalyst">System Analyst</option>
        </select>
    </form>

    <p>Email : {{ stringEmail }}</p>
    <p>Password : {{ stringPassword }}</p>
    <p>Role App : {{ roleProfesi }}</p>
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
            roleProfesi: '',
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
input,
select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}
</style>
