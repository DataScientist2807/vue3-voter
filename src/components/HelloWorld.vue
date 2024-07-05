<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-xl-4 offset-xl-4">
        <div class="card mt-5">
          <div class="card-header">
            <h2 class="card-title">Stimme jetzt ab!</h2>
          </div>
          <div class="card-body">
            <div class="d-flex">
              <div class="d-shrink-0">
                <img src="https://via.placeholder.com/60" alt="" />
              </div>
              <div class="flex-grow-1 ms-3">
                <h5>
                  Spaghetti Bolognese
                  <span class="float-end text-primary" style="cursor: pointer"
                    ><i class="fa fa-chevron-up"></i> <strong>16</strong></span
                  >
                </h5>
                <div>Eine Nudelgericht mit Hackfleischsoße.</div>
                <small class="text-muted">Eingereicht von: Italien</small>
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
      submissions: [
        {
          id: 1,
          title: "Spaghetti Bolognese",
          desc: "Ein Nudelgericht mit Hackfleischsoße.",
          votes: 16,
          author: "Italien",
          img: "https://via.placeholder.com/64",
        },
        {
          id: 2,
          title: "Wiener Schnitzel",
          desc: "Ein dünnes Schnitzel aus Kalbfleisch.",
          votes: 5,
          author: "Österreich",
          img: "https://via.placeholder.com/64",
        },
        {
          id: 3,
          title: "Peking-Ente",
          desc: "Das kaiserliche Gericht.",
          votes: 20,
          author: "China",
          img: "https://via.placeholder.com/64",
        },
        {
          id: 4,
          title: "Gulasch",
          desc: "Ein traditionelles Ragout.",
          votes: 24,
          author: "Ungarn",
          img: "https://via.placeholder.com/64",
        },
      ],
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
