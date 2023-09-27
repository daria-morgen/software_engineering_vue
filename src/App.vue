<template>
  <div class="head_block">
    <ul v-for="comp in components" v-bind:key="comp">
      <li>
        {comp}
      </li>
    </ul>
    <table>
      <tr>
        <th>
          <button v-on:click="counter -= 1" :disabled='counter === 0'>previous</button>
        </th>
        <th>
          <LastName v-if="counter == 0"></LastName>
          <FirstName v-if="counter == 1"></FirstName>
          <MiddleName v-if="counter == 2"></MiddleName>
          <ArticleName v-if="counter == 3"></ArticleName>
          <JournalName v-if="counter == 4"></JournalName>
          <VolumeComponent v-if="counter == 5"></VolumeComponent>
          <IssueComponent v-if="counter == 6"></IssueComponent>
          <PagesComponent v-if="counter == 7"></PagesComponent>
        </th>
        <th>

          <button v-on:click="counter += 1" :disabled='counter === 7'>next</button>
        </th>
      </tr>
    </table>

    <hr>
    <div>
      <div>
        <!--         вида: «[AuthorLastName], [AFN]. [AMN].
        [ArticleName] / [AFN]. [AMN]. [AuthorLastName] // [Journal Name]. – Vol.
        [Volume]. – Iss. [Issue]. – Pp. [Pages]».-->
        <span v-if="isShow">«[
          <LastName></LastName>
          ],
          [
          <FirstName></FirstName>
          ].
          [
          <MiddleName></MiddleName>
          ].
          [
          <ArticleName></ArticleName>
          ]/
          [
          <FirstName></FirstName>
          ].
          [
          <MiddleName></MiddleName>
          ].
          [
          <LastName></LastName>
          ]//
          [
          <JournalName></JournalName>
          ]. - vol.
          [
          <VolumeComponent></VolumeComponent>
          ]. --Iss.
          [
          <IssueComponent></IssueComponent>
          ]. - Pp.
          [
          <PagesComponent></PagesComponent>
          ]»
        </span>
      </div>
      <br>
      <div>
        <button v-on:click="isShow=!isShow">Показать/скрыть</button>
      </div>
    </div>
  </div>
</template>

<script>
import ArticleName from './components/ArticleName.vue'
import FirstName from './components/FirstName.vue'
import IssueComponent from './components/IssueComponent.vue'
import JournalName from './components/JournalName.vue'
import LastName from './components/LastName.vue'
import MiddleName from './components/MiddleName.vue'
import PagesComponent from './components/PagesComponent.vue'
import VolumeComponent from './components/VolumeComponent.vue'

export default {
  name: 'App',
  components: {
    LastName,
    FirstName,
    MiddleName,
    ArticleName,
    JournalName,
    VolumeComponent,
    IssueComponent,
    PagesComponent
  },
  data() {
    return {
      counter: 0,
      isShow: false
    }
  },


}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  /*text-align: center;*/
  color: #2c3e50;
  margin-top: 60px;
}

#app th {
  width: 100px;
  height: 50px;
}
</style>
