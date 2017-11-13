<template>
  <div>
    <q-card v-for="(memory, index) in memories" :key="memory.date" :memoryIndex="index">
      <q-item>
        <q-item-side :avatar="memory.user.avatar" />
        <q-item-main>
          <q-item-tile label>{{ memory.user.displayedName }}</q-item-tile>
          <q-item-tile sublabel><q-icon name="location_on" color="blue" />{{ memory.location.state }} . {{ memory.location.city }} . {{ memory.location.place }}</q-item-tile>
        </q-item-main>
      </q-item>
      <q-card-main>
        {{ memory.description }}
        <q-item-tile sublabel> Published : {{ memory.date | moment("from") }}</q-item-tile>
      </q-card-main>
      <q-gallery-carousel :src="memory.gallery" />
      <q-card-actions align="around">
        <template v-if="memory.ownLike">
          <q-btn round small flat color="red"><q-icon name="favorite_border" /></q-btn>
        </template>
        <template v-else>
          <q-btn round small flat color="black"><q-icon name="favorite_border" /></q-btn>
        </template>
        <q-btn round small flat color="green"><q-icon name="explore" /></q-btn>
        <q-btn round small flat color="blue" @click="openCommentModal()"><q-icon name="comment" /></q-btn>
        <q-modal ref="commentsModal">
          <q-modal-layout>
            <q-toolbar slot="header">
              <q-btn flat @click="$refs.commentsModal[index].close()">
                <q-icon name="keyboard_arrow_left" />
              </q-btn>
              <div class="q-toolbar-title">
                Comments
              </div>
            </q-toolbar>
            <div class="layout-padding">
              <q-chat-message :name="memory.user.displayedName" :avatar="memory.user.avatar" :text="text" stamp="4 minutes ago" sent />
              <q-chat-message :name="memory.user.displayedName" :avatar="memory.user.avatar" :text="text" stamp="4 minutes ago" />
            </div>
            <q-toolbar slot="footer">
              <div class="q-toolbar-title">
                <q-input v-model="text" placeholder="Your comment" />
              </div>
            </q-toolbar>
          </q-modal-layout>
        </q-modal>
      </q-card-actions>
    </q-card>
  </div>
</template>

<script>
import { QInput, QChatMessage, QModal, QModalLayout, QToolbar, QCard, QCardMedia, QCardTitle, QCardSeparator, QCardMain, QGalleryCarousel, QItem, QItemSide, QItemMain, QItemTile, QCardActions, QBtn, QIcon } from 'quasar'

export default {
  data () {
    return {
      text: [
        'Hi'
      ],
      memoryIndex: 0,
      memories: [
        {
          user: {
            displayedName: 'Douz12',
            name: 'Naris Raz',
            avatar: 'https://cmkt-image-prd.global.ssl.fastly.net/0.1.0/ps/2698155/1160/772/m1/fpnw/wm0/supertramp-2017-.jpg?1494963184&s=0b92c85a15996f9dd8f0c4eee8c16f07'
          },
          location: {
            place: 'Vieux Port',
            country: '',
            city: 'Marseille',
            state: 'France'
          },
          ownLike: true,
          date: Date.now(),
          gallery: [
            'https://imghtlak.mmtcdn.com/blog/sites/default/files/road-trip-indian-license.jpg',
            'https://pre00.deviantart.net/e478/th/pre/i/2012/191/f/7/trip_to_dabravino___the_path_in_the_forest_by_thegoldeagle-d56olmu.jpg'
          ]
        },
        {
          user: {
            displayedName: 'Naris Raz',
            name: 'Naris Raz',
            avatar: 'https://cmkt-image-prd.global.ssl.fastly.net/0.1.0/ps/2698155/1160/772/m1/fpnw/wm0/supertramp-2017-.jpg?1494963184&s=0b92c85a15996f9dd8f0c4eee8c16f07'
          },
          location: {
            place: 'Vieux Port',
            country: '',
            city: 'Marseille',
            state: 'France'
          },
          ownLike: false,
          description: 'Cool pics from my trip in France',
          date: Date.now(),
          gallery: [
            'https://imghtlak.mmtcdn.com/blog/sites/default/files/road-trip-indian-license.jpg',
            'https://pre00.deviantart.net/e478/th/pre/i/2012/191/f/7/trip_to_dabravino___the_path_in_the_forest_by_thegoldeagle-d56olmu.jpg'
          ]
        }
      ]
    }
  },
  components: {
    QInput, QChatMessage, QModal, QModalLayout, QToolbar, QCard, QCardMedia, QCardTitle, QCardSeparator, QCardMain, QGalleryCarousel, QItem, QItemSide, QItemMain, QItemTile, QCardActions, QBtn, QIcon
  },
  methods: {
    openCommentModal () {
      this.$nextTick(() => {
        this.$refs.commentsModal[this.memoryIndex].open()
      })
    }
  }
}
</script>

<style>
</style>
