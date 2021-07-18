<template>
  <form>
      <label>Email: </label>
      <input type="email" required v-model="email">

      <label>Password: </label>
      <input type="password" required v-model="password">
  
    <label>Role: </label>
    <select v-model="role">
        <option value="developer">Web developer</option>
        <option value="designer">Web designer</option>
    </select>

    <label>Skills:</label>
    <input type="text" v-model="tempSkill" @keyup.alt="addSkill">
    <div v-for="skill in skills" :key="skill" class="pill" @click="deleteSkill(skill)">
        {{ skill }}
    </div>

    <div class="terms">
        <input type="checkbox" required v-model="terms">
        <label>Accept term and conditions</label>
    </div>
    
    <div class="submitButton">
        <button>Submit</button>
    </div>

  </form>
</template>

<script>
export default {
    data() {
        return {
            email: '',
            password: '',
            role: 'designer',
            terms: false,
            tempSkill: '',
            skills: []
        }
    },
    methods: {
        addSkill(e) {
            if (e.key === ',' && this.skills) {
                if (!this.skills.includes(this.tempSkill)) {
                    this.skills.push(this.tempSkill)
                }

                this.tempSkill = ''
            }
        },
        deleteSkill(skill) {
            this.skills = this.skills.filter((item) => {
                return item !== skill
            })
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
        color: #aaa;
        display: inline-block;
        margin: 25px 0 15px;
        font-size: 0.6em;
        text-transform: uppercase;
        letter-spacing: 1px;
        font-weight: bold;
    }

    input, select {
        display: block;
        padding: 10px 6px;
        width: 100%;
        box-sizing: border-box;
        border: none;
        border-bottom: 1px solid #ddd;
        color: #555;
    }

    input[type="checkbox"] {
        display: inline-block;
        width: 16px;
        margin:  0 10px 0 0;
        position: relative;
        top: 2px;
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
        width: 150px;
        height: 45px;
        margin: 50px auto;
        background: dodgerblue;
        color: black;
        border: none;
        border-radius: 10px;
        letter-spacing: 0.2em;
        font-size: 80%;
        font-weight: bold;
        cursor: pointer;
    }

    .submitButton {
        text-align: center;
    }
</style>