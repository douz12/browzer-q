
<template>
  <div class="layout-padding">
    <q-card v-for="(memory, index) in memories" :key="memory.id" :memoryIndex="index">
      <q-item>
        <q-item-side :avatar="memory.user.avatar" />
        <q-item-main>
          <q-item-tile label>{{ memory.user.displayName }}</q-item-tile>
          <q-item-tile sublabel><q-icon name="location_on" color="blue" />{{ memory.location.state }} . {{ memory.location.city }} . {{ memory.location.place }}</q-item-tile>
        </q-item-main>
      </q-item>
      <q-card-main>
        {{ memory.description }}
        <q-item-tile sublabel>{{ memory.date | moment("from") }}</q-item-tile>
      </q-card-main>
      <q-gallery-carousel :src="memory.gallery" />
      <q-card-actions align="around">
        <template v-if="isLiked(memory)">
          <q-btn round small flat color="red" @click="like(memory)"><q-icon name="favorite_border" />
            {{ memory.likes.length }}
          </q-btn>
        </template>
        <template v-else>
          <q-btn round small flat color="grey-13" @click="like(memory)"><q-icon name="favorite_border" />
            {{ memory.likes.length }}
          </q-btn>
        </template>
        <q-btn round small flat color="grey-13"><q-icon name="explore" /></q-btn>
        <q-btn round small flat color="grey-13" @click="openCommentModal(index)"><q-icon name="comment" />
          {{ memory.commentsCount }}
        </q-btn>
        <q-btn round small flat color="grey-13" @click="openCommentModal(index)"><q-icon name="remove_red_eye" />
          {{ memory.gallery.length }}
        </q-btn>
      </q-card-actions>
      <q-modal ref="commentsModal">
        <q-modal-layout>
          <q-toolbar slot="header">
            <q-btn flat @click="closeCommentModal()">
              <q-icon name="keyboard_arrow_left" />
            </q-btn>
            <div class="q-toolbar-title">
              Comments
            </div>
          </q-toolbar>
          <div slot="footer">
            <q-input placeholder="Your comment..." v-model="newComment" :after="[
              {
                icon: 'send'
              }
            ]"
            />
          </div>
          <div>
            <MemoryComments :memoryId="memory.id" />
          </div>
        </q-modal-layout>
      </q-modal>
    </q-card>
  </div>
</template>

<script>
import MemoryComments from '@/MemoryComments.vue'
import { QList, QInput, QModal, QModalLayout, QToolbar, QCard, QCardMedia, QCardTitle, QCardSeparator, QCardMain, QGalleryCarousel, QItem, QItemSide, QItemMain, QItemTile, QCardActions, QBtn, QIcon } from 'quasar'

export default {
  data () {
    return {
      newComment: '',
      currentUser: {
        id: '1'
      },
      memoryIndex: 0,
      memories: [
        {
          id: '1',
          user: {
            displayName: 'Douz12',
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
          ],
          likes: [
            '1', '2'
          ],
          commentsCount: 3
        },
        {
          id: '2',
          user: {
            displayName: 'Naris Raz',
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
          ],
          likes: [
            '2'
          ],
          commentsCount: 3
        }
      ]
    }
  },
  components: {
    QList, MemoryComments, QInput, QModal, QModalLayout, QToolbar, QCard, QCardMedia, QCardTitle, QCardSeparator, QCardMain, QGalleryCarousel, QItem, QItemSide, QItemMain, QItemTile, QCardActions, QBtn, QIcon
  },
  methods: {
    openCommentModal (index) {
      this.memoryIndex = index
      this.$nextTick(() => {
        this.$refs.commentsModal[this.memoryIndex].open()
      })
    },
    closeCommentModal () {
      this.$nextTick(() => {
        this.$refs.commentsModal[this.memoryIndex].close()
      })
    },
    isLiked (memory) {
      return memory.likes.indexOf(this.currentUser.id) === 0
    },
    like (memory) {
      if (this.isLiked(memory)) {
        // TODO remove user id
      }
      else {
        // TODO add user id
      }
    }
  }
}
</script>

<style>
</style>