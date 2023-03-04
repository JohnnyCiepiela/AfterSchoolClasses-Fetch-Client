<template>
  <div v-for="lesson in searchResults" class="float_child">
    <figure>
      <img v-bind:src="lesson.image" width="100px" height="=100px" />
    </figure>

    <h1 v-text="lesson.title"></h1>
    <p><b>Location:</b> {{ lesson.location }}</p>
    <p><b>Description:</b> {{ lesson.description }}</p>
    <p><b>Price:</b> {{ lesson.price }}</p>

    <button v-on:click="addItemToCart(lesson)" v-if="canAddToCart(lesson)">
      Add to the Cart
    </button>

    <button v-else disabled>Add to the Cart</button>

    <!--Conditions regarding the product availability display-->
    <span v-if="classesLeft(lesson) === 0"> All out!</span>

    <span v-else-if="classesLeft(lesson) < 4">
      Only {{ classesLeft(lesson) }} left!</span
    >

    <span v-else> Buy now!</span>

    <!--Simple rating system-->
    <div>
      <span v-for="n in lesson.rating"> ★ </span>
      <span v-for="n in 5 - lesson.rating"> ☆ </span>
    </div>
  </div>
</template>

<script>
export default {
    name: "LessonsList",
    props: ["sortedLessons", "imagesBaseURL"],
    data() {
        return {

        }
    },
}
</script>
