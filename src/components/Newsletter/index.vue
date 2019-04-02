<template>
    <div class="container newsl_container">
        <h2>Join our newsletter</h2>
        <div class="form">
            <input type="text" v-model="email"/>
            <button @click="submitHandler">Subscribe</button>
        </div>
        <div class="error_label">
            <div>{{ error }}</div>
        </div>
        <div class="success_label">
            <div>{{ success }}</div>
        </div>
        <div class="small">
            Lorem ipsum dolor sit amet consectetur, adipisicing elit. Consectetur doloremque praesentium voluptate amet. Quos porro ratione odio molestias animi at molestiae suscipit nemo, cumque aperiam ab incidunt voluptate exercitationem ut.
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            email:'',
            error:'',
            success:''
        }
    },
    methods: {
        validate(email) {
            let valid = [true, ''];

            if(!/\S+@\S+\.\S+/.test(email)) {
                valid = [false, 'Please enter a valid email'];
                this.email = '';
            };

            if(email === '') {
                valid = [false, `It's empty`]
            };

            return valid;
        },
        submitHandler() {
            let valid = this.validate(this.email);

            if(valid[0]) {
                this.error = '';
                this.addEmail(this.email)
            } else {
                this.error = valid[1]
            };
        },
        addEmail(email) {
            this.$http.get(`users.json?orderBy=\"email\"&&equalTo=\"${email}\"`)
            .then( response => {
                if(Object.getOwnPropertyNames(response.data).length === 0) {
                    this.$http.post('users.json', {email: this.email})
                    .then (response => {
                        this.success = 'Thank you';
                        this.email = '';
                    })
                } else {
                    this.success = "User has already subscribed";
                    this.email = '';
                }
            });
        }
    }
}
</script>
