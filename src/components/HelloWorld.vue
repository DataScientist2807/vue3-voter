<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-xl-4 offset-xl-4">
        <div class="card mt-5">
<!--           <div class="card-header" v-bind:class="{ 'bg-primary': totalVotes > 50, 'text-white': totalVotes > 50 }"> -->  
          <div class="card-header" v-bind:class="cardHeaderBackgroundColor">
            <h2 class="card-title">
              Stimme jetzt ab!
              <span class="float-end">{{ totalVotes }} Stimmen</span>
            </h2>
          </div>
          <div class="card-body">
            <template v-for="(submission) in sortedSubmissions"
            :key="submission.id">
              <div
                class="d-flex" 
              >
                <div class="d-shrink-0">
                  <img v-bind:src="submission.img" alt="" />
                </div>
                <div class="flex-grow-1 ms-3">
                  <h5>
                    {{ submission.title }}
                    <span
                      class="float-end text-primary"
                      style="cursor: pointer"
                      v-on:click="upvote(submission.id)"
                      ><i class="fa fa-chevron-up"></i>
                      <strong>{{ submission.votes }} </strong></span
                    >
                  </h5>
                  <div>{{ submission.desc }}</div>
                  <small class="text-muted"
                    >Eingereicht von: {{ submission.desc }}</small
                  >
                </div>
              </div>
              <hr />
            </template>

           
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Voter",
  data() {
    return {
      submissions: [
        {
          id: 1,
          title: "Spaghetti Bolognese",
          desc: "Ein Nudelgericht mit Hackfleischsoße.",
          votes: 16,
          author: "Italien",
          img: "bolognese.jpg",
        },
        {
          id: 2,
          title: "Wiener Schnitzel",
          desc: "Ein dünnes Schnitzel aus Kalbfleisch.",
          votes: 5,
          author: "Österreich",
          img: "schnitzel.jpg",
        },
        {
          id: 3,
          title: "Peking-Ente",
          desc: "Das kaiserliche Gericht.",
          votes: 20,
          author: "China",
          img: "ente.jpg",
        },
        {
          id: 4,
          title: "Gulasch",
          desc: "Ein traditionelles Ragout.",
          votes: 1,
          author: "Ungarn",
          img: "gulasch.jpg",
        },
      ],
    };
  },
  computed: {
    sortedSubmissions() {
      return [...this.submissions].sort((a, b) => {
        return b.votes - a.votes;
      });
    },
    totalVotes() {
      return this.submissions.reduce((totalVotes, submission) => {
        return totalVotes + submission.votes;
      }, 0);
    },
    cardHeaderBackgroundColor() {
      /* return {
        'bg-primary': this.totalVotes >= 50,
        'text-white':  this.totalVotes >= 50
        Alternative
        'bg-primary text-white': this.totalVotes >= 50
      } */
        // Array schreibweise
        if (this.totalVotes >= 50) {
          return ['bg-primary', 'text-white']
        } else {
          return []
        }
    }
  },
  methods: {
    upvote(submissionId) {
      const submission = this.submissions.find(
        (submission) => submission.id === submissionId
      );
      submission.votes++;
    },
  },
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
