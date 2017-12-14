<template>
	<div class="container">
	<div>
		<h3>What is your goal?</h3>
		<b-form-checkbox id="weightLoss"
											v-model="goal"
											value='loseWeight'
											unchecked-value=false>
				Lose Weight
			</b-form-checkbox>
			<b-form-checkbox id="improveHealth"
											v-model="goal"
											value='health'
											unchecked-value=false>
				Improve Health
			</b-form-checkbox>
			<b-form-checkbox id="improvedPerformance"
											v-model="goal"
											value='performance'
											unchecked-value=false>
				Improve Performance
			</b-form-checkbox>
	</div>

<!-- Improve Health -->
<div v-if="this.goal === 'health'">
<h3>What would you like to acheive?</h3>
<b-form-checkbox id="flexibility"
                     v-model="flexibility"
                     value=true
                     unchecked-value=false>
      Improve Flexibility
    </b-form-checkbox>
		<b-form-checkbox id="feelBetter"
                     v-model="feelBetter"
                     value=true
                     unchecked-value=false>
      Feel Better
    </b-form-checkbox>
		<b-form-checkbox id="decreasePain"
                     v-model="decreasePain"
                     value=true
                     unchecked-value=false>
      Decrease Chronic Pain
    </b-form-checkbox>
</div>

<!-- Weight Loss Section -->

	<div v-if="this.goal ==='loseWeight'">
		<h3>How much would you like to lose?</h3>
		<b-container fluid>
			<b-row class="my-1">
					<b-form-input v-model="lossGoal" id="input-default" type="text" placeholder="20 lbs"></b-form-input>
			</b-row>
		</b-container>
	</div>

	<!-- Time Line for Weight Loss -->

	<div v-if="this.lossGoal !== ''">
		<h3>How Much Would You Want to Lose per Week</h3>
		<b-form-checkbox id="onePoundLoss"
                     v-model="weeklyLoss"
                     value=1
                     unchecked-value=false>
      < 1 lb per week (safe)
    </b-form-checkbox>
		<b-form-checkbox id="twoPoundLoss"
                     v-model="weeklyLoss"
                     value=2
                     unchecked-value=false>
      2 lbs per week (recommended)
    </b-form-checkbox>
		<b-form-checkbox id="threePoundLoss"
                     v-model="weeklyLoss"
                     value=3
                     unchecked-value=false>
			 > 3s lb per week (risky)
    </b-form-checkbox>
		<h4 v-if="this.weeklyLoss !== null">At this rate it will take {{ (this.lossGoal / this.weeklyLoss).toFixed(1) }} weeks to reach your goal</h4>
		<b-btn v-if="this.weeklyLoss !== null" class="btn">Next Step</b-btn>
	</div>
	
	<!-- Of the Goals what Improved Performance Category would you like? -->

	<div v-if="this.goal === 'performance'">
		<h3>What interests you more?</h3>
	    <b-form-checkbox id="strength"
                     v-model="strength"
                     value=true
                     unchecked-value=false>
      Strength Work
    </b-form-checkbox>
		 <b-form-checkbox id="aerobic"
                     v-model="aerobic"
                     value=true
                     unchecked-value=false>
      Aerobic Work
    </b-form-checkbox>
	</div>
		<!-- Strength Section -->

		<div v-if="this.strength === 'true'">
			<h3>How Often Would You like to be in the Gym? </h3>
			<b-form-checkbox
				id="fullBody"
				v-model="fullBody">
				Less then twice a week
			</b-form-checkbox>
			<b-form-checkbox
				id="sectionalWO"
				v-model="sectionalWO">
				More then three times a week
			</b-form-checkbox>
		</div>

		<!-- Aerobic Section -->

		<div v-if="this.aerobic === 'true'">
		<h3>What aspect of Aerobics are you Interested In? </h3>
				<b-form-checkbox
					id="cycling"
					value="cycling"
					v-model="cycling">
					Cycling
				</b-form-checkbox>
				<b-form-checkbox
					id="running"
					value="running"
					v-model="running">
					Running
				</b-form-checkbox>
				<b-form-checkbox
					id="general"
					value="general"
					v-model="general">
					General
				</b-form-checkbox>
		</div>

		<!--== Prefered Workout type is Cycling ==-->

		<div v-if="this.cycling === 'cycling'">
			<h3>What Would you like to focus on in Cycling</h3>
			<b-form-checkbox
					id="half-century"
					value="half-century"
					v-model="cyclingGoal">
					50 miler
			</b-form-checkbox>
			<b-form-checkbox
					id="metric-century"
					value="metric-century"
					v-model="cyclingGoal">
					Metric Century (60 miler)
				</b-form-checkbox>
				<b-form-checkbox
					id="century"
					value="century"
					v-model="cyclingGoal">
					Full Century (100 big ones)
				</b-form-checkbox>
				<b-btn v-if="this.cyclingGoal !== ''" class="btn">Next Step</b-btn>
		</div>

		<!--== Prefered Workout Type is Running ==-->

		<div v-if="this.running === 'running'">
			<h3>What Would you like to focus on in Running</h3>
			<b-form-checkbox
					id="5k"
					value="5k"
					v-model="runGoal">
					5k
			</b-form-checkbox>
			<b-form-checkbox
					id="10k"
					value="10k"
					v-model="runGoal">
					10K
				</b-form-checkbox>
				<b-form-checkbox
					id="halfMarathon"
					value="halfMarathon"
					v-model="runGoal">
					Half Marathon
				</b-form-checkbox>
				<b-form-checkbox
					id="marathon"
					value="marathon"
					v-model="runGoal">
					Marathon
				</b-form-checkbox>
				<br>
				<b-btn v-if="this.runGoal !== ''" class="btn">Next Step</b-btn>
		</div>

		<!--== Prefered Workout Type is General ==-->

		<div v-if="this.general === 'general'">
			<h3>What Interests you more?</h3>
			<b-form-checkbox
					id="stretching"
					value=true
					v-model="stretching">
					Stretching
			</b-form-checkbox>
			<b-form-checkbox
					id="strengthMaintenance"
					value=true
					v-model="strengthMaintenance">
					Strength Maintenance
				</b-form-checkbox>
				<br>
				<b-btn class="btn">Next Step</b-btn>
		</div>

	<!-- If Cycling Goal is Century -->
	<div>

	</div>

	</div>
</template>

<script>
	export default {
  name: 'hello',
  data () {
     return{
        strength: false,
				aerobic: false,
				test1: 'something',
				cycling: '',
				running: '',
				general: '',
				cyclingGoal: '',
				fullBody: false,
				sectionalWO: false,
				stretching: false,
				strengthMaintenance: false,
				goal: '',
				lossGoal: '',
				runGoal: '',
				weeklyLoss: null,
				flexibility: false,
				feelBetter: false,
				decreasePain: false,
        }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	h1,
	h2 {
		font-weight: normal;
	}

	ul {
		list-style-type: none;
		padding: 0;
	}

	li {
		display: inline-block;
		margin: 0 10px;
	}

	a {
		color: #42b983;
	}
	.btn{
		border: 1px solid black;
		padding: 1.75vh 8vw;
		font-weight: bolder;
		margin-top: 5vh;
	}
	.btn:hover{
		background-color: black;
		color: white;
	}
</style>