<template>
  <div id="app">
    <LikeHeader>
      <h1>こんにちは。</h1>
    </LikeHeader>
    <button @click="currentComponent = 'Home'">Home</button>
    <button @click="currentComponent = 'About'">About</button>
    <button @click="currentComponent = 'Test'">Test</button>

    <!-- コンポーネントの切り替えを動的に行うにはcomponetsタグを使用することでできる -->
    <!-- componentsタグが指定したコンポーネントになるイメージ -->
    <!-- コンポーネント v-bind:is='データ'の形 -->
    <!-- 下記のように文字列のしても可能。 -->

    <!-- <components :is="'About'"></components>
    <components :is="'Home'"></components> -->

    <!-- 動的コンポーネントの注意点として、コンポーネントの切り替えを行うとインスタンスがdestroyされる -->
    <!-- つまり初期化されてしまうので、form等に値を入れた状態で切り替えを行うと、値が失われる挙動になる -->

    <!-- 上記対策としてはkeep-aliveタグでcomponetsタグを囲ってあげることで解決する -->

    <!-- keep-aliveを使うと新しいライフサイクルフックdeactivated・activatedが追加される -->
    <!-- keep-alive使用しているコンポーネントでcreatedを使用したい時はactivatedを使用する-->
    <!-- keep-alive使用しているコンポーネントでdestroyを使用したい時はdeactivated を使用する-->

    <keep-alive>
      <components v-bind:is="currentComponent"></components>
    </keep-alive>

    <!-- <components :is="currentComponent"></components> -->

    <!-- v-ifを使ってコンポーネントの切り替えを行う方法 -->
    <!-- <About v-if="currentComponent === 'About'"></About>
    <Home v-if="currentComponent === 'Home'"></Home> -->

  </div>
</template>

<script>
import LikeHeader from './components/LikeHeader.vue'
import About from './components/About.vue'
import Home from './components/Home.vue'
import Test from './components/Test.vue'

export default {
  components: {
    LikeHeader,
    About,
    Home,
    Test,
  },
  data() {
    return {
      number: 10,
      currentComponent: "",
    }
  }
}
</script>

