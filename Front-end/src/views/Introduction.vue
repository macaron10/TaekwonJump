<template>
  <div>
    <div>
      <v-item-group mandatory active-class="primary">
        <v-row
          class="justify-center"
          style="background-color:rgb(245, 245, 247, 0.7)"
        >
          <v-btn-toggle v-model="toggle_exclusive" mandatory>
            <v-col
              class="text-center"
              v-for="(menu, i) in menus"
              :key="menu.title"
              style="background-color:rgb(245, 245, 247, 0.7)"
            >
              <v-btn
                active-class="no-active"
                text
                @click="Window = i"
                style="outline:none"
              >
                <v-img
                  v-if="Window == i"
                  height="50px"
                  width="50px"
                  :src="menu.imgPath2"
                ></v-img>
                <v-img
                  v-else
                  height="50px"
                  width="50px"
                  :src="menu.imgPath"
                ></v-img>
              </v-btn>
              <div
                v-if="Window == i"
                style="color:rgb(0, 112, 201)"
                class="text-caption"
              >
                {{ menu.title }}
              </div>
              <div v-else class="text-caption">{{ menu.title }}</div>
            </v-col>
          </v-btn-toggle>
        </v-row>
      </v-item-group>
    </div>

    <v-container style="width: 63rem;">
      <v-window v-model="Window">
        <v-window-item v-for="n in length" :key="n">
          <Intro v-show="Window == 0" />
          <History v-show="Window == 1" />
          <Technique v-show="Window == 2" />
          <Category v-show="Window == 3" />
        </v-window-item>
      </v-window>
    </v-container>
  </div>
</template>

<script>
import Intro from "../components/Introduction/Intro.vue";
import History from "../components/Introduction/History.vue";
import Category from "../components/Introduction/Category.vue";
import Technique from "../components/Introduction/Technique.vue";

export default {
  name: "introduction",
  components: {
    Intro,
    History,
    Category,
    Technique,
  },
  data() {
    return {
      menus: [
        {
          title: "소개",
          imgPath: require("./../assets/class-img/img-class1.png"),
          imgPath2: require("./../assets/class-img/img-class1-a.png"),
        },
        {
          title: "역사",
          imgPath: require("./../assets/class-img/img-class2.png"),
          imgPath2: require("./../assets/class-img/img-class2-a.png"),
        },
        {
          title: "기술 체계",
          imgPath: require("./../assets/class-img/img-class3.png"),
          imgPath2: require("./../assets/class-img/img-class3-a.png"),
        },
        {
          title: "용어 사전",
          imgPath: require("./../assets/class-img/img-class4.png"),
          imgPath2: require("./../assets/class-img/img-class4-a.png"),
        },
      ],
      model: 0,
      length: 4,
      Window: 0,
      toggle_exclusive: undefined,
    };
  },
};
</script>

<style scoped>
.v-btn--active.no-active::before {
  background-color: transparent !important;
}
</style>
