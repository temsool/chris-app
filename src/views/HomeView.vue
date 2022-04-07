<template>
  <v-card>
    <v-card-header>
      <v-card-avatar>
        <v-avatar image="../assets/avatar.jpg"></v-avatar>
      </v-card-avatar>

      <v-card-header-text>
        <v-card-title size="large">Hey Chris! 👋</v-card-title>
      </v-card-header-text>
    </v-card-header>
    <v-card-text>
      <v-card color="#FAFAFA" class="pa-4 mt-2 mb-2">
        <v-chip class="current-amount" color="purple" label text-color="white">
          <v-icon start icon="mdi-currency-gbp"></v-icon> 105,000
        </v-chip>
        <v-row class="mt-4">
          <v-col cols="10">
            <v-progress-linear
              striped
              rounded
              v-model="remainingTarget"
              color="orange"
              height="36"
            >
              <template v-slot:default="{ value }">
                <strong>{{ Math.ceil(value) }}%</strong>
              </template>
            </v-progress-linear></v-col
          >

          <v-col cols="2" class="d-flex align-center justify-end"
            ><span class="acc-amount">£1M</span>
            <span style="font-size: 30px; line-height: 1">🎯</span>
          </v-col>
        </v-row>
      </v-card>
      <v-card color="#E8F5E9" class="pa-4 mt-2 mb-2">
        <v-row align="center">
          <v-col cols="9" class="d-flex align-center">
            <v-avatar size="40px">
              <v-img
                class="acc-img"
                alt="Avatar"
                src="https://acc2021.a2c2.org/sites/acc21/files/styles/large/public/images/logos/ISA-color-logo-tm-300dpi-413x382.png?itok=tPockTUX"
              ></v-img>
            </v-avatar>

            <Popper placement="right" hover content="ISA Account">
              <div class="acc-title ml-4">ISA</div>
            </Popper>
          </v-col>
          <v-col cols="3" class="d-flex align-center justify-end"
            ><span class="acc-amount"> £100,000</span></v-col
          >
        </v-row>
      </v-card>

      <v-card color="#DCEDC8" class="pa-4 mt-2 mb-2">
        <v-row align="center">
          <v-col cols="9" class="d-flex align-center">
            <v-avatar size="40px">
              <v-img
                class="acc-img"
                alt="Avatar"
                src="https://res.cloudinary.com/crunchbase-production/image/upload/c_lpad,h_170,w_170,f_auto,b_white,q_auto:eco,dpr_1/vnzn2eo2soiqdoyu4zz1"
              ></v-img>
            </v-avatar>

            <Popper placement="right" hover content="SIPP">
              <div class="acc-title ml-4">SIPP</div>
            </Popper>
          </v-col>
          <v-col cols="3" class="d-flex align-center justify-end"
            ><span class="acc-amount"> £15,000</span></v-col
          >
        </v-row>
      </v-card>

      <v-card color="#C5E1A5" class="pa-4 mt-2 mb-2">
        <v-row align="center">
          <v-col cols="9" class="d-flex align-center">
            <v-avatar size="40px">
              <v-img
                class="acc-img"
                alt="Avatar"
                src="https://upload.wikimedia.org/wikipedia/commons/thumb/5/5f/Piggy_Bank_or_Savings_Flat_Icon_Vector.svg/1200px-Piggy_Bank_or_Savings_Flat_Icon_Vector.svg.png"
              ></v-img>
            </v-avatar>

            <Popper placement="right" hover content="Lifetime ISA">
              <div class="acc-title ml-4">LISA</div>
            </Popper>
          </v-col>
          <v-col cols="3" class="d-flex align-center justify-end"
            ><span class="acc-amount">£4,000</span></v-col
          >
        </v-row>
      </v-card>

      <v-card color="#AED581" class="pa-4 mt-2 mb-2">
        <v-row align="center">
          <v-col cols="9" class="d-flex align-center">
            <v-avatar size="40px">
              <v-img
                class="acc-img"
                alt="Avatar"
                src="https://cdn.stevenstone.co.uk/website_steven_stone/static/src/images/gia/img-gia-emblem.png"
              ></v-img>
            </v-avatar>

            <Popper placement="right" hover content="GIA">
              <div class="acc-title ml-4">GIA</div>
            </Popper>
          </v-col>
          <v-col cols="3" class="d-flex align-center justify-end"
            ><span class="acc-amount">£2,000</span></v-col
          >
        </v-row>
      </v-card>

      <v-card color="#9CCC65" class="pa-4 mt-2 mb-2">
        <v-row align="center">
          <v-col cols="9" class="d-flex align-center">
            <v-avatar size="40px">
              <v-img
                class="acc-img"
                alt="Avatar"
                src="https://bitcoin.org/img/icons/opengraph.png?1648897668"
              ></v-img>
            </v-avatar>

            <Popper placement="right" hover content="Crypto.com">
              <div class="acc-title ml-4">Crypto</div>
            </Popper>
          </v-col>
          <v-col cols="3" class="d-flex align-center justify-end"
            ><span class="acc-amount"> £1,000</span></v-col
          >
        </v-row>
      </v-card>
      <div class="mx-auto d-flex">
        <Chart
          :size="{ width: 800, height: 400 }"
          :data="this.plByMonth"
          :margin="this.margin"
          :direction="this.direction"
        >
          <template #layers>
            <Grid strokeDasharray="2,2" />
            <Line :dataKeys="['name', 'pl']" />
          </template>
        </Chart>
      </div>
    </v-card-text>
  </v-card>
</template>
<style lang="scss" scoped>
:deep(.popper) {
  background: #e92791;
  padding: 20px;
  border-radius: 20px;
  color: #fff;
  font-weight: bold;
  text-transform: uppercase;
}

:deep(.popper #arrow::before) {
  background: #e92791;
}

:deep(.popper:hover),
:deep(.popper:hover > #arrow::before) {
  background: #e92791;
}
.acc-title {
  font-size: 30px;
  font-weight: bold;
}
.current-amount {
  font-size: 20px;
  font-weight: bold;
  padding: 25px 10px;
}
.acc-amount {
  font-size: 30px;
  font-weight: bold;
}
.total-money-wrap {
  font-size: 40px;
}
</style>
<script>
import { Chart, Grid, Line } from "vue3-charts";

export default {
  name: "HomeView",
  components: {
    Chart,
    Grid,
    Line,
  },
  data() {
    return {
      direction: "horizontal",
      margin: {
        left: 0,
        top: 20,
        right: 20,
        bottom: 0,
      },
      plByMonth: [
        { name: "Jan", pl: 1000, avg: 500, inc: 300 },
        { name: "Feb", pl: 2000, avg: 900, inc: 400 },
        { name: "Apr", pl: 400, avg: 400, inc: 500 },
        { name: "Mar", pl: 3100, avg: 1300, inc: 700 },
        { name: "May", pl: 200, avg: 100, inc: 200 },
        { name: "Jun", pl: 600, avg: 400, inc: 300 },
        { name: "Jul", pl: 500, avg: 90, inc: 100 },
      ],
      remainingTarget: 30,
    };
  },
};
</script>

