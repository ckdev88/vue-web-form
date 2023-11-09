<!-- 11.35 - 11.55 -->
<!-- 1960@11.37 -->
<template>
	<form @submit.prevent="handleSubmit">
		<label>Email:</label>
		<input type="email" v-model="email" />
		<label>Password:</label>
		<input type="password" required v-model="password" />
		<div v-if="passwordError" class="error">{{ passwordError }}</div>
		<label>Role:</label>
		<select v-model="role">
			<option value="developer">Web developer</option>
			<option value="designer">Designer</option>
		</select>
		<div>
			<label>Skills</label>
			<input type="text" v-model="tempSkill" @keyup="addSkill" />
		</div>

		<div>
			<label><input type="checkbox" required v-model="terms" /> accept terms
				and conditions</label>
		</div>
		<div class="submit">
			<button>Submitbutton</button>
		</div>
		<input type="submit" />
	</form>
	<div class="summary">
		E-mail: {{ email }}<br />
		Password: {{ password }}<br />
		Role: {{ role }}<br />
		Terms accepted: {{ terms }}<br />
		Skills: {{ skills }}<br />
		Skills list:
		<!-- <div v-for="skill in skills" :key="skill" class="pill" @click="removeSkill(skill)">{{ skill }}</div> -->
		<div v-for="(skill, index) in skills" :key="index" class="pill" @click="removeSkill2(index)">
			{{ skill }}
		</div>
		<!-- stukje schoner om gewoon index te gebruiken, als key en als index voor removeSkill2 -->
	</div>
</template>

<script>
export default {
	data() {
		return {
			greeting: 'aloha',
			email: '',
			password: '',
			role: '',
			terms: false,
			tempSkill: '',
			skills: [],
			passwordError: '',
		};
	},
	methods: {
		sanitizeSkill(skill) {
			let ret = skill.trim();
			ret = ret.slice(0, -1);
			ret = ret.trim();
			return ret;
		},
		addSkill(e) {
			if ((e.key === ',' || e.key === ';') && this.tempSkill.length > 2) {
				this.tempSkill = this.sanitizeSkill(this.tempSkill);
				if (!this.skills.includes(this.tempSkill)) {
					this.skills.push(this.tempSkill);
				}
				console.log('this.skills:', this.skills);
				this.tempSkill = '';
			}
		},
		removeSkill(skill) {
			this.skills.splice(this.skills.indexOf(skill), 1); // op basis van inhoud in de array
		},
		removeSkill2(i) {
			this.skills.splice(i, 1); // op basis van de index in de array
		},
		handleSubmit() {
			this.passwordError =
				this.password.length < 6 ? 'This is too short' : '';
			if (!this.passwordError) {
				console.log('this.email:', this.email)
				console.log('this.password:', this.password)
				console.log('this.role:', this.role)
				console.log('this.skills:', this.skills)
				console.log('this.terms:', this.terms)
			}
		},
	},
};
</script>

<style>
.summary {
	font-style: italic;
}

form {
	max-width: 30rem;
	margin: 2rem auto;
	background: black;
	text-align: left;
	padding: 1rem;
	border-radius: 0.5rem;
}

label {
	display: block;
	margin: 2rem 0 1rem;
	text-align: left;
	text-transform: uppercase;
}

input[type='text'],
input[type='password'],
input[type='email'],
select {
	display: block;
	padding: 0.6rem 0.4rem;
	width: 100%;
	box-sizing: border-box;
}

.error {
	color: red;
}

.pill {
	background: #555;
	border-radius: 0.3rem;
	padding: 0.3rem;
	display: inline-block;
	margin: 0.1rem 0.1rem 0 0;
	cursor: pointer;
}

.submit button {
	font-size: 1.2rem;
	padding: 0.6rem;
	border-radius: 0.5em;
	background-color: silver;
	color: black;
	font-weight: bold;
	cursor: pointer;
	text-transform: uppercase;
	transition: background-color 0.2s ease-in-out;
}

.submit button:hover {
	background-color: ivory;
}
</style>
