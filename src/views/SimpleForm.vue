<script setup lang="ts">

const data = reactive({
    categories: [
        'sustainability',
        'nature',
        'animal welfare',
        'housing',
        'education',
        'food',
        'community'
    ],
    event: {
        category: '',
        title: '',
        description: '',
        location: '',
        pets: 1,
        extras: {
            catering: false,
            music: false
        }
    }
})

</script>

<template>
  <div>
    <h1>Create an event</h1>
    <form>

      <label>Select a category</label>
      <select v-model="data.event.category">
        <option
          v-for="option in data.categories"
          :value="option"
          :key="option"
          :selected="option === data.event.category"
        >{{ option }}</option>
      </select>

      <h3>Name & describe your event</h3>

      <label>Title</label>
      <input
        v-model="data.event.title"
        type="text"
        placeholder="Title"
        class="field"
      >

      <label>Description</label>
      <input
        v-model="data.event.description"
        type="text"
        placeholder="Description"
        class="field"
      />

      <h3>Where is your event?</h3>

      <label>Location</label>
      <input
        v-model="data.event.location"
        type="text"
        placeholder="Location"
        class="field"
      />

      <h3>Are pets allowed?</h3>
      <div>
        <input
            type="radio"
            v-model="data.event.pets"
            :value="1"
            name="pets"
          />
        <label>Yes</label>
      </div>

      <div>
        <input
          type="radio"
          v-model="data.event.pets"
          :value="0"
          name="pets"
        />
        <label>No</label>
      </div>

      <h3>Extras</h3>
      <div>
        <input
          type="checkbox"
          v-model="data.event.extras.catering"
          class="field"
        />
        <label>Catering</label>
      </div>

      <div>
        <input
          type="checkbox"
          v-model="data.event.extras.music"
          class="field"
        />
        <label>Live music</label>
      </div>

      <button type="submit">Submit</button>
    </form>

    <pre>{{ data.event }}</pre>
  </div>
</template>