<script>
import Home from '@/components/Home.vue'
import Intro from '@/components/Intro.vue'
import Forms from '@/components/Form.vue'
import Notice from '@/components/Notice.vue'

export default {
  name: 'app',
  components: {
    Home,
    Intro,
    Forms,
    Notice
  },
  data () {
    return {
      isModalVisible: false,
    };
  },
  methods: {
    showModal() {
      this.isModalVisible = true;
    },
    closeModal() {
      this.isModalVisible = false;
    }
  },
};

</script>

<template>
  <div id="bg" class="fixed inset-0 -z-10 bg-cover bg-center"></div>
  <div id="bg-wrapper" class="fixed inset-0 -z-10 bg-black opacity-50"></div>

  <div class=" relative min-h-screen z-10">
    <Home />
    <Intro />
    <Intro />
    <div class="relative z-20 flex items-center justify-center h-screen">
      <Forms class="relative z-10" @openModal="showModal"/>
      <Notice class="absolute" v-show="isModalVisible" :isModalVisible="isModalVisible" @close="closeModal"/>
    </div>
  </div>

</template>

<style>
#bg {
  background-image: url('@/assets/img/bg.jpg');
}
</style>
