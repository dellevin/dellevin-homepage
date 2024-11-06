<template>
  <div></div>
</template>

<script>
export default {
  name: "MyBookmarks",
  data() {
    return {
      htmlContent: "",
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
            let htmlContent = data; // 将内容赋值给 htmlContent
            //   console.log(this.htmlContent); 
            let jsonBookMarks = this.bookmarksHtmlToJson(htmlContent)
            console.log(jsonBookMarks)
        })
        .catch((err) => {
          console.error("Error loading HTML file:", err);
        });
    },
    bookmarksHtmlToJson(html) {
      // 使用 DOMParser 解析 HTML
      const parser = new DOMParser();
      const doc = parser.parseFromString(html, 'text/html');

      // 递归函数解析 <DL> 和 <DT> 标签
      const parseNode = (node) => {
        let items = [];
        node.childNodes.forEach(child => {
          if (child.tagName === 'DT') {
            const anchor = child.querySelector('a');
            if (anchor) {
              // 获取书签的标题和 URL
              items.push({
                title: anchor.textContent,
                url: anchor.href
              });
            }
            const subFolder = child.querySelector('h3');
            const dl = child.querySelector('dl');
            if (subFolder && dl) {
              // 解析文件夹及其内容
              items.push({
                folder: subFolder.textContent,
                children: parseNode(dl)
              });
            }
          }
        });
        return items;
      };

      // 从根 <DL> 标签开始解析
      const rootDl = doc.querySelector('dl');
      return parseNode(rootDl);
    }
  },
};
</script>

<style scoped></style>
