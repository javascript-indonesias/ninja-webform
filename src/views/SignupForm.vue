<template>
    <form action="" @submit.prevent="handleSubmitEvent">
        <label for="emailinput">Email</label>
        <input type="email" required id="emailinput" v-model="stringEmail" />

        <label for="passwordinput">Password</label>
        <input type="password" required v-model="stringPassword" id="passwordinput" />
        <div v-if="passwordError" class="errorclass">{{ passwordError }}</div>

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
            <span @click="deleteSkill(skill)">
                {{ skill }}
            </span>
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

        <!-- Membuat tombol submit kirim -->
        <div class="submit">
            <button>
                Daftarkan Akun
            </button>
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
            passwordError: '',
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
        deleteSkill(skillItem) {
            this.listSkills = this.listSkills.filter((item) => {
                // Jika nilai tidak sama, maka ada di dalam array
                // Jika nilai sama, maka return false, dan dihilangkan dari array
                return skillItem !== item;
            });
        },
        handleSubmitEvent() {
            // validasi password dan kata sandi
            this.passwordError =
                this.stringPassword.length > 5 ? '' : 'Panjang kata sandi minimal 5 karakter';

            if (!this.passwordError) {
                console.log('email', this.stringEmail);
                console.log('password', this.stringPassword);
                console.log('role', this.roleProfesi);
                console.log('skills', this.listSkills);
                console.log('Pilihan akun', this.listAkunCheck);
                console.log('terms setuju', this.termsAccept);
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

.pill {
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
}

button {
    background: #0b6dff;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: #fff;
    border-radius: 20px;
    font-weight: bold;
}

.submit {
    text-align: center;
}

.errorclass {
    color: #ff0062;
    margin-top: 10px;
    font-size: 0.8em;
    font-weight: bold;
}
</style>
