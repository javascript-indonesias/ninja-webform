<template>
    <form action="">
        <label for="emailinput">Email</label>
        <input type="email" required id="emailinput" v-model="stringEmail" />

        <label for="passwordinput">Password</label>
        <input type="password" required v-model="stringPassword" id="passwordinput" />

        <!-- Select options dengan menggunakan Vue model -->
        <label for="">Role Developer</label>
        <select name="selectrole" id="selectrole" v-model="roleProfesi">
            <option value="" disabled>Select Role</option>
            <option value="webdeveloper">Web Developer</option>
            <option value="webdesigner">Web Designer</option>
            <option value="qa">Quality Assurance</option>
            <option value="systemanalyst">System Analyst</option>
        </select>

        <!-- Key Event Modifiers -->
        <label for="inputskill">Keahlian Skill</label>
        <input
            type="text"
            name="inputskill"
            id="inputskill"
            v-model="inputSkillTemp"
            @keyup.alt="addSkillKeahlian"
        />

        <div v-for="skill in listSkills" :key="skill" class="pill">
            {{ skill }}
        </div>

        <!-- Menggunakan Checkbox dan multi checkbox -->
        <div class="terms">
            <input type="checkbox" required id="inputcheckbox" v-model="termsAccept" />
            <label for="inputcheckbox">Setuju dengan syarat dan ketentuan yang berlaku</label>
        </div>

        <p>Jenis Akun</p>
        <div>
            <input type="checkbox" v-model="listAkunCheck" id="namecheckbox" value="premium" />
            <label for="namecheckbox">Akun Premium</label>
        </div>
        <div>
            <input type="checkbox" v-model="listAkunCheck" id="namecheckbox" value="silver" />
            <label for="namecheckbox">Akun Silver</label>
        </div>
        <div>
            <input type="checkbox" v-model="listAkunCheck" id="namecheckbox" value="free" />
            <label for="namecheckbox">Akun Free</label>
        </div>
    </form>

    <p>Email : {{ stringEmail }}</p>
    <p>Password : {{ stringPassword }}</p>
    <p>Role App : {{ roleProfesi }}</p>
    <p>Terms Disetujui : {{ termsAccept }}</p>
    <p>Daftar Akun Pilihan : {{ listAkunCheck }}</p>
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
            termsAccept: false,
            listAkunCheck: [],
            inputSkillTemp: '',
            listSkills: [],
        };
    },
    methods: {
        addSkillKeahlian(event) {
            // Tambahkan skill setelah diketik koma
            // Agar koma tidak masuk ke dalam skill, gunakan
            // event modifier dengan menekan Alt key + comma dulu
            // baru fungsi ini kembali berjalan
            if (event.key === ',' && this.inputSkillTemp) {
                if (!this.listSkills.includes(this.inputSkillTemp)) {
                    // Tambahkan ke dalam array
                    this.listSkills.push(this.inputSkillTemp);
                }
                this.inputSkillTemp = '';
            }
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
    font-size: 0.7em;
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

input[type='checkbox'] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 4px;
}
</style>
