<template>
        <div class="d-flex">
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

</template>

<script>
    export default {
        name: "SubmissionListItem",
        props: ['submission'],
    }
</script>
