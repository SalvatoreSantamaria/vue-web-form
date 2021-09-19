<template> https://youtu.be/ixOcve5PX-Q?t=1216
    <div>
        <!-- prevent is event modifier that prevents default action of event being sumitted -->
        <form @submit.prevent="handleSubmit">
            <label>Email: </label> 
            <!-- Two way data binding one: v-model= will connect and update to the data property email -->
            <input type="email" required v-model="email">

            <label>Password: </label>
            <input type="password" required v-model="password">

            <label>Role:</label>
            <select v-model="role">
                <option value="developer">Developer</option>
                <option value="designer">Designer</option>
            </select>

            <div class="terms">
                <input type="checkbox" v-model="checkbox" required>
                <label>Accept Terms and Conditions</label>
            </div>

        <div>
            <!-- Use value="" to assign a value to the v-model, as the v-model is an array and there are multiple inputs -->
            <input type="checkbox" value="Kuma" v-model="names">
            <label>Kuma</label>
        </div>
        <div>
            <input type="checkbox" value="Mona" v-model="names">
            <label>Mona</label>
        </div>
        <div>
            <input type="checkbox" value="Raven" v-model="names">
            <label>Raven</label>
        </div>

        <label>Enter Skills</label>
        <!-- keyboard event uses @. also keypress and keydown -->
        <input 
            type="text" 
            v-model="tempSkill" 
            @keyup="addSkill"
            placeholder="Type skill and press ,"
        > <!-- @keyup.alt is an event modifier, preventing comma from displaying when pressing alt-->
        <div v-for="skill in skills" :key="skill" class="pill"><!-- bind using : -->
            <div @mousedown="deleteSkill(skill)">
                {{ skill }}
            </div>
        </div>

        <div class="submit">
            <button>Create an Account</button>
        </div>

        </form>
    </div>
    <p>Email: {{ email }}</p>
    <p>Password: {{ password }}</p>
    <p>Role: {{ role }}</p>
    <p>Checkbox: {{ checkbox }}</p>
    <p>Names: {{ names }}</p>

</template>

<script>
export default {
    data() {
        return {
            email: '', // Two way data binding two: data is updated by the v-model
            password: '',
            role: '',
            checkbox: false,
            names: [],
            tempSkill: "",
            skills: [],
        }
    },
    methods: {
        addSkill(event) { //the event object fires automatically whenever an event fires
            //console.log(event)
            if (event.key === ',' && this.tempSkill) {
                if (!this.skills.includes(this.tempSkill)) {
                    this.skills.push(this.tempSkill)
                    console.log('this.skills ', this.skills)
                }
                this.tempSkill = ''
            }
        },
        deleteSkill(skill) {
            this.skills = this.skills.filter((item) => {
                return skill !== item
            })
        },
        handleSubmit() {
            console.log('Form Submitted')
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
    input, select {
        display: block;
        padding: 10px 6px;
        width: 100%;
        box-sizing: border-box;
        border: none;
        border-bottom: 1px solid #ddd;
        color: #555;
    }

    input[type="checkbox"] { /* Targeting input where the type is checkbox */
        display: inline-block;
        width: 16px;
        margin: 0 10px 0 0;
        position: relative;
        top: 2px;
    }

    /* makes text output look like a pill instead of plain words */
    .pill {
        display:inline-block;
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
        background: blue;
        border: 0;
        padding: 10px 20px;
        margin-top: 20px;
        color: white;
        border-radius: 20px;
    }

    .submit {
        text-align: center;
    }

</style>