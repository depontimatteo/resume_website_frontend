<template>
	<div class="container">
		<div class="hero">
			<h1 class="name"><strong>{{first_name}}</strong> {{last_name}}</h1>
			<span class="job-title">{{role}}</span>
			<span class="email">{{mail}}</span>

			<h2 class="lead">{{bio_short}}</h2>
		</div>
	</div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'Contacts',
    props: {
        language_id: String
    },
    data() {
        return {
            first_name: '',
            last_name: '',
            role: '',
            bio_short: '',
            linkedin: '',
            twitter: '',
            web: '',
            mail: ''
        }
    },
    mounted() {
        axios.get('http://127.0.0.1:5000/get_bio/' + this.language_id)
        .then(response => {
            this.linkedin = response.data.linkedin,
            this.twitter = response.data.twitter,
            this.web = response.data.web,
            this.mail = response.data.mail,
            this.first_name = response.data.first_name,
            this.last_name = response.data.last_name,
            this.role = response.data.role,
            this.bio_short = response.data.bio_short
        })
        .catch(err => {
            this.linkedin = err
        });

    }
}
</script>

<style scoped>
.container {
	max-width: 1100px;
	height: auto;
	margin: 60px auto;
}

.hero {
	margin: 50px auto; 
	position: relative;
}

h1.name {
	font-size: 70px;
	font-weight: 300;
	display: inline-block;
}

.job-title {
	vertical-align: top;
	background-color: #D9E7F8;
	color: #4A90E2;
	font-weight: 600;
	margin-top: 5px;
	margin-left: 20px;
	border-radius: 5px;
	display: inline-block;
	padding: 15px 25px;
}

.email {
	display: block;
	font-size: 24px;
	font-weight: 300;
	color: #81899C;
	margin-top: 10px;
}

.lead {
	font-size: 44px;
	font-weight: 300;
	margin-top: 60px;
	line-height: 55px;
}
</style>

