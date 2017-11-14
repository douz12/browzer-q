
<template>
  <div>
    <q-list>
      <q-item v-for="(comment, index) in memoryComments" :key="index" multiline>
        <q-item-side>
          <q-item-tile avatar>
            <img :src="comment.user.avatar" />
          </q-item-tile>
        </q-item-side>
        <q-item-main>
          <q-item-tile label>
            {{ comment.user.displayName }}
          </q-item-tile>
          <q-item-tile sublabel>
            {{ comment.text[0] }}
            <p class="comment-date">{{ comment.date | moment("from") }}</p>
          </q-item-tile>
        </q-item-main>
      </q-item>
    </q-list>
  </div>
</template>

<script>
import { QList, QItemMain, QItemTile, QItemSide, QItem, QItemSeparator } from 'quasar'

export default {
  props: ['memoryId'],
  data () {
    return {
      memoryComments: [
        {
          user: {
            id: '1',
            displayName: 'bob',
            avatar: 'https://cmkt-image-prd.global.ssl.fastly.net/0.1.0/ps/2698155/1160/772/m1/fpnw/wm0/supertramp-2017-.jpg?1494963184&s=0b92c85a15996f9dd8f0c4eee8c16f07'
          },
          text: [
            'Nice place to go'
          ],
          date: Date.now()
        },
        {
          user: {
            id: '2',
            displayName: 'John',
            avatar: 'https://cmkt-image-prd.global.ssl.fastly.net/0.1.0/ps/2698155/1160/772/m1/fpnw/wm0/supertramp-2017-.jpg?1494963184&s=0b92c85a15996f9dd8f0c4eee8c16f07'
          },
          text: [
            'Cool'
          ],
          date: Date.now()
        }
      ]
    }
  },
  components: {
    QList, QItemMain, QItemTile, QItemSide, QItem, QItemSeparator
  }
}
</script>

<style lang="stylus">
.comment-date
  padding-top: 5px
  font-size: small
  opacity: 0.7
</style>