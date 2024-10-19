<!--ttps://play.vuejs.org/#eNqdVtty2zYQ/ZUNZzpKbFH0JW1nFLnT1JOHNNO4sf3SsfxAkysJMQQwBCjfxv/egwsp0nHaTF5IEHs7uzi74EPytqomm4aTaTKzvK5kbvm3uSKalWJDm1QsjubJF6VpRl8aNlZoZSaS1dKu5olXjKqFzI1xuo24TwutbC4U150OtF6kKR03dc3K0lmha6Y03UqrzsOVlmVq+dbC+B/d1FREI+OMpvTwEFb0+Ei6saQXbuspOkhnWfV89E9R9zsAdKouBMqwS/vw7EF0ES8guOziDSKe5qXQdNVYCz1aaCSz0qJgMwgdSg0pgr8MCmMSquTbV3i1JvOEptd8Bx0v6pUWLmR+xbK3gS2hqsb2d4jsXcWwrx2qeTKUTTe5bJw0hHsq3qRrXbKE3LDkwnL5Vpkbd8J9vWwAAUUKzlCcHtZsCHaWIf+nhTv5EKs2KFTc+r2QorgGFIVDak8I9Tj5MMuCSsvM6Lq/CoF8kE/gKh1rsJ6RD0hZM3cB46mwNKEhvsGRtGbTSEeVFiU4S6t8w1R0nu2KQRdx/4JmpspxotFLp5E6acv3wO6b3Hw/1SezzDnu0o7Ej7nG3GdZr8PxaYpaVBZrvq10bankRY5U6MEZqXyNXhthPIzG7rvMbf7yVZAR1WybGk3R5owOmNLemLKsa7IWZSByqxh7eKjqNzuNAb2mpBopvfZZFFAeiNeGbqsxpYvRL7RDv9LRaEyjg0PXrHvh4xwHEMzIauIN13d2JdSShBldeu8tjUzrdxn0vdvXB87J4aF7Yh0sjjXQFzb67exitzqzPae/7x/e9KmDOArcWOC8WHWpBFePb9z70Vd/zXalSziNFe8Tf3sq6D/nlYtrEgtPupizMCCjR9sqQv4SFTCTYbnp6OgIhthv07/wX27C9cJgknhbd267ux6nR7xtYgD5S6MHUG2Hw+HdMsKNwcj8rjVawzacd9vzdsqGwZQhB3zpBr4Hbp7m5rkU0Ya6uqerM9qnbQbXGPZOuh6ZdF0eUl/gWktvWCxXdkpO5n35XSPuQev9g72f3lC2Q3iTzOslou5kCOHcbr3FmfG/Thf5Wsg7dOG5WIMnH/mGTvU6V2CR3xmjHrVYeINCS41uWboR9hWsnyMsvL+GNbyx0a64Ni6GN8VlD2oH6hizSsAAsAAofo1prZXGLCrYR2w5jmusp9+LPhyBz8X58eTdMU5J2BzXhUfz3i9RkxJlMJaqHGMvYgEF4rHPVTJOLMitFmI5+Wy0wt+RBxYmtpBcn1RhWCRdS86TXEp986ffs3XDnmDexnXkM/ufDS7xKRZ/gw9cb3DndjLrTgm3ihO/O/vof0Y6IW7iRkL7P4RoFy2bcC86tT8aVQJ2T8+jfb92kx+D8Ny8u7WsTJuUA7odP/MEv4juovxW6lu4h5PX3g41TR7/Bc6ETvc= -->
<template>
  <div v-if="qno < questions.length">
    <div class="quiz-container">
      <!-- Current Score -->
      <p class="bold-text">Your current score: {{ score }} out of {{ questions.length }}</p>
      <!-- Current Question -->
      <p class="bold-text">Question {{ qno + 1 }}: {{ questions[qno] }}</p>

      <!-- Radio buttons for choices -->
      <div v-for="(choice, index) in choices" :key="index">
        <label>
          <input
            type="radio"
            :value="choice"
            v-model="selectedAnswer"
          />
          {{ choice }}
        </label>
      </div>

      <!-- OK button -->
      <button @click="nextQuestion">OK</button>
    </div>
  </div>
  

  <!-- Quiz Completed Screen -->
  <div v-else>
     <p class="bold-text-result">
      You have completed the quiz! <span class="completed-quiz">Your score was {{ score }} out of {{ questions.length }}.</span>
    </p>
   

  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      qno: 0, // Current question index
      score: 0, // Current score
      selectedAnswer: null, // Selected answer
      questions: ['6 * 7 =', '23 + 10 =', '4*6', 'The answer to everything is'], // Questions
      ganswers: ['42', '33', '24', '42'], // Correct answers
      choices: ['0', '1', '24', '33', '42'], // Choices for each question
    };
  },
  methods: {
    nextQuestion() {
      // Check if the answer is correct
      if (this.selectedAnswer === this.ganswers[this.qno]) {
        this.score++;
      }

      // Move to the next question or complete the quiz
      this.qno++;

      // Reset selected answer for next question
      this.selectedAnswer = null;
    },
  },
};
</script>

<style>
.bold-text {
  font-weight: bold;
  font-size: 120%; /* 20% larger */
}

.bold-text-result {
  font-weight: bold;
  font-family: 'Times New Roman', Times, serif;
  color: green;
  font-size: 150%; /* 50% larger */
}

.quiz-container input[type="radio"] {
  font-family: 'Courier New', Courier, monospace; /* Choices in Courier New */
}

.completed-quiz {
  font-family: 'Times New Roman', Times, serif;
  color: green;
  font-style: italic; /* Italicized last part */
}
</style>

