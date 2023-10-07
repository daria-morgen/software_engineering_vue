<template>
  <div>
    <table>
      <tr>
        <th>
          <button @click="previousItem" :disabled='count === 0'>previous</button>
        </th>
        <th>
          <span>{{ title }}</span>
          <input v-model="titleValue" autofocus :disabled='count === 8'/>
        </th>
        <th>
          <button @click="nextItem" :disabled='count === 8'>next</button>
        </th>
      </tr>
    </table>
    <hr>
    <span>{{ authorLink }}</span>
    <br>
    <button @click="showAuthorLink">Отобразить ссылку</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
      titleList: ["First name",
        "Last name",
        "Middle name",
        "Article name",
        "Journal name",
        "Volume",
        "Issue",
        "Pages"
      ],
      title: "First name",
      titleValue: "",
      authorData: new Map(),
      authorLink: ""
    }
  },
  methods: {
    nextItem() {
      if (this.titleValue !== "") {
        this.authorData.set(this.title, this.titleValue)
      }

      this.count++
      this.title = this.titleList[this.count]
      this.titleValue = ""
    },
    previousItem() {
      this.count--
      this.title = this.titleList[this.count]
      this.titleValue = this.authorData.get(this.title)

    },
    showAuthorLink() {
      // «[AuthorLastName], [AFN]. [AMN].
      // [ArticleName] / [AFN]. [AMN]. [AuthorLastName]
      // [Journal Name]. – Vol.[Volume]. – Iss. [Issue]. – Pp. [Pages]».
      if (this.authorData.size === this.titleList.length)
        this.authorLink = "«" + this.authorData.get("Last name")
            + ", " + this.authorData.get("First name")[0]
            + ". " + this.authorData.get("Middle name")[0]

            + ". " + this.authorData.get("Article name")
            + " / " + this.authorData.get("First name")[0]
            + ". " + this.authorData.get("Middle name")[0]
            + ". " + this.authorData.get("Last name")

            + " " + this.authorData.get("Journal name")
            + ". – Vol. " + this.authorData.get("Volume")
            + ". – Iss. " + this.authorData.get("Issue")
            + ". – Pp. " + this.authorData.get("Pages") + "»";
      else alert("Заполнены не все поля.")
    }

  }
}

</script>