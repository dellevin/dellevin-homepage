<template>
  <div></div>
</template>

<script>
export default {
  name: "MyBookmarks",
  data() {
    return {
        jsonBookMarks: "",
    };
  },
  mounted() {
    this.loadBookmarks();
  },
  methods: {
    loadBookmarks() {
      // 加载 bookmarks.html 文件内容
      fetch("/assets/bookmarks.html")
        .then((response) => {
          if (!response.ok) {
            throw new Error(`HTTP error! status: ${response.status}`);
          }
          return response.text();
        })
        .then((data) => {
          let jsonBookMarks = this.bookmarksHtmlToJson(data);
          console.log(jsonBookMarks);
        })
        .catch((err) => {
          console.error("Error loading HTML file:", err);
        });
    },
    bookmarksHtmlToJson(html) {
        return html;
    },
  },
};
</script>

<style scoped></style>
