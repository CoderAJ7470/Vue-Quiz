<template>
  <div id="app">
    <Header />
    <QABlock
      :currentQuestion="questions[index]"
      :next="next"
      :questionCount="questionCount"
      :totalQuestions="questions.length" />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import QABlock from './components/QABlock.vue';

export default {
  name: 'app',
  components: {
    Header,
    QABlock
  },
  methods: {
    next() {
      this.index += 1;
      this.questionCount += 1;

      if(this.index === this.questions.length) {
        alert('Quiz finished');
        this.index = 0;
        this.questionCount = 1;
      }
    }
  },
  data() {
    return {
      index: 0,
      questionCount: 1,
      questions: [
        {
          id: 1,
          value: 'What is a "wall cloud"?',
          choices: [
            {id: 1, text: 'A space on the internet which allows vertical storage'},
            {id: 2, text: 'A dark, vertical rotating cloud that is attached to the base of a supercell thunderstorm and is often the precursor to a tornado',
              isCorrect: true},
            {id: 3, text: 'A fancy term for cotton that is used for containerizing'},
            {id: 4, text: 'A section of the internet that is cordoned off for specific "club" members'}
          ],
        },
        {
          id: 2,
          value: 'In the Far East, hurricanes are more commonly known by what term?',
          choices: [
            {id: 1, text: 'Buzzsaws'},
            {id: 2, text: 'Spirals of doom',},
            {id: 3, text: 'Typhoons', isCorrect: true},
            {id: 4, text: 'One-eyed monsters'}
          ],
        },
        {
          id: 3,
          value: 'True or false: Tornadoes do not occur near rivers or lakes',
          choices: [
            {id: 1, text: 'True'},
            {id: 2, text: 'False', isCorrect: true},
          ],
        },
        {
          id: 4,
          value: 'True or false: The largest hail stone ever recorded in history was eight inches in diameter.',
          choices: [
            {id: 1, text: 'True', isCorrect: true},
            {id: 2, text: 'False'},
          ],
        },
        {
          id: 5,
          value: 'Complete the following sentence: An "overshooting top" refers to ...',
          choices: [
            {id: 1, text: '... a child\'s toy that does not stay in one place'},
            {id: 2, text: '... a T-shirt that is too "loud"'},
            {id: 3, text: '... the part of a storm that "bubbles up" over the anvil when the updraft is very strong', isCorrect: true},
            {id: 4, text: '... Marge Simpson\'s hair-do'}
          ],
        },
        {
          id: 6,
          value: 'The Storm Prediction Center is located in:',
          choices: [
            {id: 1, text: 'Stormville, NY (yes, this is an actual city)'},
            {id: 2, text: 'Truth Or Consequences, NM'},
            {id: 3, text: 'Weatherford, OK'},
            {id: 4, text: 'Norman, OK', isCorrect: true}
          ],
        },
        {
          id: 7,
          value: 'Choose the most correct answer:',
          choices: [
            {id: 1, text: 'The average lightning flash will light a 100W bulb for more than three months'},
            {id: 2, text: 'Lightning is three times hotter than the surface of the Sun (> 50,000 degrees F)'},
            {id: 3, text: 'A lightning bolt travels 90,000 miles per second (talk about lightning speed!)'},
            {id: 4, text: 'All of the above is true', isCorrect: true}
          ],
        },
        {
          id: 8,
          value: '"Freezing fog" refers to which of the following?',
          choices: [
            {id: 1, text: 'An amphibian that is in the process of hibernating for the winter'},
            {id: 2, text: 'A heavy metal band'},
            {id: 3, text: 'Your brain\'s condition after 2:30 p.m.'},
            {id: 4, text: 'Fog that freezes on exposed surfaces when the temperature is 32F or less', isCorrect: true}
          ],
        },
        {
          id: 9,
          value: 'The word "dewpoint" describes which of the following?',
          choices: [
            {id: 1, text: 'The point at which Mountain Dew tastes best'},
            {id: 2, text: 'Moisture in the air condensing to form water when the air temperature cools to this particular temperature.',
              isCorrect: true},
            {id: 3, text: 'A town in Oklahoma'},
            {id: 4, text: 'A cheap clone of a major chemical company'}
          ],
        },
        {
          id: 10,
          value: 'Complete the following sentence: "CoCoRaHS refers to..."',
          choices: [
            {id: 1, text: 'A brand of coconut rum found only in Jamaica'},
            {id: 2, text: 'Some kid trying to be the next "cool dude" with alternating capital letters'},
            {id: 3, text: 'One of the daily Jumbles in the papers'},
            {id: 4, text: 'Community Collaborative Rain, Hail and Snow network', isCorrect: true}
          ],
        }
      ]
    }
  }
}
</script>
