<template>
  <form @submit.prevent="handleSubmit">
      <label>Title:</label>
      <input type="text" v-model="title" required>
      <label>Details:</label>
      <textarea v-model="details" required></textarea>
      <button>Add Project</button>
  </form>
</template>

<script>
export default {
    data() {
        return {
            title: '',
            details: ''
        }
    },
    methods: {
        handleSubmit() {
            let project = {
                title: this.title,
                details: this.details,
                complete: false
            }

            fetch('http://localhost:3000/projects', {
                method: 'POST',
                headers: { 'Content-Type': 'application/json' },
                body: JSON.stringify(project)
            }).then(() => {
                this.$router.push('/')
            }).catch(err => console.log(err.message))
        }
    }
}
</script>

<style>
form {
    padding: 20px;
    border-radius: 10px;
    background-color: #fff;
}

label {
    display: block;
    margin: 20px 0 10px 0;
    color: #bbb;
    text-transform: uppercase;
    font-size: 14px;
    font-weight: bold;
    letter-spacing: 1px;
}

input {
    padding: 10px;
    width: 100%;
    box-sizing: border-box;
    border: 0;
    border-bottom: 1px solid #ddd;
}

textarea {
    padding: 10px;
    height: 100px;
    width: 100%;
    box-sizing: border-box;
    border: 1px solid #ddd;
}

form button {
    display: block;
    margin: 20px auto 0;
    padding: 10px;
    border: 0;
    border-radius: 6px;
    background-color: #00ce89;
    color: #fff;
    font-size: 16px;
}

form button:hover {
    cursor: pointer
}

form button:active {
    transform: scale(0.98);
}

form button:focus {
    outline: none;
}
</style>