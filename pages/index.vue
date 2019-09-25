<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-container
        class="pa-2"
        fluid
      >
        <v-row>
          <v-flex xs12 md8>
            <v-col
            v-for="card in cards"
            :key="card.title">
            <v-card>
              <v-img
                :src="card.src"
                class="white--text"
                gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              >
                <v-card-title
                  class="fill-height align-end"
                  v-text="card.title"
                ></v-card-title>
              </v-img>
            </v-card>
          </v-col>
          </v-flex>
          <v-flex xs12 md4>
            <v-col
          >
            <v-card
              class="mx-auto ma-2"
              color="secondary"
              dark
            >
              <v-card-text class="headline font-weight-bold">
                "Turns out our pies are incredible and you should buy one."
              </v-card-text>
              <v-card-actions>
                <v-list-item class="grow">
                  <v-list-item-avatar color="grey darken-3">
                    <v-img
                      class="elevation-6"
                      src="https://scontent-bru2-1.xx.fbcdn.net/v/t1.0-1/p320x320/25395844_10212800810193484_1819266099847727990_n.jpg?_nc_cat=102&_nc_oc=AQmb6ctIJ1CZTHtQrQX4q_Cd5nmsG6YFlnCbabvJCtyNOKOc4PPlc1ayVt6uAnf2NSg&_nc_ht=scontent-bru2-1.xx&oh=928c875b067b105a46c5615345c236e7&oe=5DFFA040"
                    ></v-img>
                  </v-list-item-avatar>
                  <v-list-item-content>
                    <v-list-item-title>Daniela Gonzalez</v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-card-actions>
            </v-card>
            <v-layout
              column
              justify-center
              align-center
            >
              <v-list-item class="grow">
                <v-btn
                  color="primary"
                  @click="checkout"
                >
                  Buy Now
                </v-btn>
              </v-list-item>
            </v-layout>
          </v-col>
          </v-flex>
        </v-row>
    </v-container>
  </v-layout>
</template>

<script>
  export default {
    data: () => ({
      cards: [
        {
          title: 'Pumpkin Cheesecake',
          src: 'https://img.sndimg.com/food/image/upload/c_thumb,q_80,w_485,h_273/v1/img/recipes/44/69/72/picmZSsfm.jpg',
          flex: 12
        },
      ],
    }),
    mounted() {

    },
    methods: {
      checkout() {
        var stripe = window.Stripe(process.env.STRIPE_KEY);
        // When the customer clicks on the button, redirect
        // them to Checkout.
        stripe.redirectToCheckout({
          items: [{sku: 'sku_FsB1j6BpU56r0M', quantity: 1}],
          successUrl: 'https://pies-by-naan.com/success',
          cancelUrl: 'https://pies-by-naan.com/canceled',
        })
      }
    }
  }
</script>
