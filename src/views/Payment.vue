<template>
  <div class="payment">
    <v-subheader>Payment Information</v-subheader>
    <v-card flat>
    <v-container>
      <table class="v-datatable v-table">
      <tbody>
      <tr><th class="column text-xs-left">Order ID</th><td>{{ payment.order_id }}</td></tr>
      <tr><th class="column text-xs-left">Invoice Number</th><td>{{ payment.invoice_number }}</td></tr>
      <tr><th class="column text-xs-left">Total Bill</th><td>Rp. {{ payment.total_bill.toLocaleString('id-ID') }}</td></tr>
      </tbody>
      </table>
    </v-container>
    </v-card>

    <v-subheader>Transfer To</v-subheader>
    <v-card flat>
    <v-container>
      <table class="v-datatable v-table">
      <tbody>
        <tr>
            <td><img src="img/bca.png" width="100px"></td>
            <td>BANK BCA No.Rek 52711155 a/n PT.BukaBuku Digital</td>
        </tr>
        <tr>
            <td><img src="img/mandiri.png" width="100px"></td>
            <td>BANK MANDIRI No.Rek 5511223366 a/n PT.BukaBuku Digital</td>
        </tr>
      </tbody>
      </table>
    </v-container>
    </v-card>

    <v-subheader></v-subheader>
    <v-card>
    <v-container>
    <v-layout row wrap>
      <v-flex xs12 text-xs-center>
      <v-btn color="success" @click="finish">
          Finish
      </v-btn>
      </v-flex>
    </v-layout>
    </v-container>
    </v-card>
  </div>
</template>
<script>
  import { mapGetters } from 'vuex'
  export default {
    computed: {
      ...mapGetters({
        payment  : 'payment',
      }),
    },
    methods: {
        finish(){
            this.$router.push('/')
        }
    },
  }
</script>