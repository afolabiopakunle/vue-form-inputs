<template>
    <form @submit="handleSubmit">
        <label for="email">Email</label>
        <input v-model="email" type="email" name="email" id="email" required />

        <label for="password">Password</label>
        <input v-model="password" type="password" name="password" id="password" required />
        <label for="role">Role</label>
        <select name="role" id="role" v-model="role">
            <option value="designer">Designer</option>
            <option value="developer">Developer</option>
        </select>
        <div class="terms">
            <label for="terms">Terms & Conditions</label>
            <input type="checkbox" name="terms" id="terms" v-model="terms">
        </div>
        <div>
            <label for="seun">Seun</label>
            <input type="checkbox" name="seun" id="seun" v-model="names" value="Seun">
            <label for="ada">Ada</label>
            <input type="checkbox" name="ada" id="ada" v-model="names" value="Ada">
            <label for="dada">Dada</label>
            <input type="checkbox" name="dada" id="dada" v-model="names" value="Dada">
        </div>
        <label for="tempSkill">Skills</label>
        <input v-model="tempSkill" type="text" name="tempSkill" id="tempSkill" @keyup="addSkill" required />
        <span v-for="skill in skills" :key="skill" class="pill" @click="removeSkill(skill)">
            {{ skill }}
        </span>

        <button class="submit">Submit</button>
    </form>
    <div>
        {{ email }} {{ password }} {{ role }} {{ terms }} {{ names }} {{ skills }}
    </div>
</template>
<script>
export default {
    data() {
        return {
            email: '',
            password: '',
            role: '',
            terms: '',
            names: [],
            tempSkill: '',
            skills: []
        }
    },
    methods: {
        addSkill(e) {
            if (e.key === ',' || e.key === 'Enter' && this.tempSkill) {
                let value = e.target.value
                if (this.skills.includes(value)) {
                    this.tempSkill = null;
                    return
                }
                if (e.key === ',') {
                    value = value.slice(0, -1);
                    if (this.skills.includes(value)) {
                        this.tempSkill = null;
                        return
                    }
                    this.skills.push(value)
                    console.log(value);
                    this.tempSkill = null;
                    return
                }
                console.log(value);
                this.skills.push(value)
                this.tempSkill = null;
            }
        },

        removeSkill(skillInput) {
            this.skills = this.skills.filter(skill => skill !== skillInput)
        },

        handleSubmit(e) {
            e.preventDefault();
            console.log(e);
        }
    },
}
</script>
<style scoped>
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
    cursor: pointer;
}

input,
select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #DDDDDD;
    color: #555555;
}

input[type='checkbox'] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
    left: 8px;
}

.pill {
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background-color: #EEEEEE;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777777;
    cursor: pointer;
}

button {
    background-color: #0B6DFF;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: white;
    border-radius: 20px;
    cursor: pointer;
}

.submit {
    text-align: center;
}
</style>