<template>
    <div class="container w-75">
        <form class="text-white">
            <div class="form-group">
                <label>Name</label>
                <input type="text" v-model="form.name" class="form-control">
            </div>
            <div class="form-group text-white">
                <label for="exampleInputEmail1">Email address</label>
                <input v-model="form.email" type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email">
            </div>
            <div class="form-group">
                <label for="exampleInputPassword1">Password</label>
                <input v-model="form.password" type="password" name="password" class="form-control" id="exampleInputPassword1" placeholder="Password">
            </div>
            <div class="form-group">
                <label for="exampleInputPassword2">Confirm Pass</label>
                <input type="password" class="form-control" name="password_confirmation" v-model="form.password_confirmation" id="exampleInputPassword2" placeholder="Password">
            </div>
            <button type="submit" @click.prevent="saveForm" class="btn btn-primary">register</button>
        </form>
    </div>
</template>

<script>
export default {
    data(){
        return {
            form: {
                name: '',
                email: '',
                password: '',
                password_confirmation: ''
            },
            errors: []
        }
    },
    methods: {
        saveForm(){
            axios.post('/api/register', this.form).then(() => {
                console.log('register saved')
                this.$router.push({name: 'Dashboard'})
            }).catch(error => {
                this.errors = error.response.data.errors;
            })
        }
    }
}
</script>

<style scoped>

</style>
