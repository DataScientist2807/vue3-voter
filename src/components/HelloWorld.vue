<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-xl-4 offset-xl-4">
        <div class="card mt-5">
          <div class="card-header">
            <h2 class="card-title">
              Stimme jetzt ab!
              <span class="float-end">{{ totalVotes }} Stimmen</span>
            </h2>
          </div>
          <div class="card-body">
            <div class="d-flex"   v-for="(submission, index) in sortedSubmissions" :key="submission.id">
              <div class="d-shrink-0">
                <img v-bind:src="submission.img" alt="" />
              </div>
              <div class="flex-grow-1 ms-3">
                <h5>
                  {{ submission.title }} {{ index }}
                  <span
                    class="float-end text-primary"
                    style="cursor: pointer"
                    v-on:click="upvote()"
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
      totalVotes: 0,
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
          votes: 24,
          author: "Ungarn",
          img: "gulasch.jpg",
        },
      ],
    };
  },
  computed:{
    sortedSubmissions() {
      return this.submissions.sort((a, b) => {
        return b.votes - a.votes;
      });
    },
  },
  methods: {
    upvote() {
      this.submissions[0].votes++;
    },
  },
  watch: {
    submissions: {
      handler(newValue, oldValue) {
        console.log(newValue)
        console.log(oldValue)
        this.totalVotes = this.submissions.reduce((totalVotes, submission) => {
          return totalVotes + submission.votes
        }, 0)
      },
      deep: true,
      immediate: true,
    },
    totalVotes(newValue, oldValue) {
      console.log(newValue);
      console.log(oldValue);
    }
  }
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
