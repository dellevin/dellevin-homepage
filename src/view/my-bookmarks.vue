<template>
    <div class="bookmarks-container">

    </div>
</template>


<script>
import { load } from "cheerio";

export default {
  name: "MyBookmarks",
  data() {
    return {
      jsonBookMarks: [],
      defaultIcon: "https://blog.ittoolman.com/usr/plugins/Handsome/assets/image/nopic.jpg",
    };
  },
  mounted() {
    this.loadBookmarks();
  },
  methods: {
    processBookmarksJson(jsonBookMarks) {
      if(jsonBookMarks.length < 1){
        return
      }
      console.log(jsonBookMarks);

      // 收集所有 "folder" 项的 "children" 中 type 为 "site" 的项
      const sites = jsonBookMarks
        .filter(item => item.type === "folder")  // 只选择 type 为 "folder" 的项
        .flatMap(folder => folder.children || [])  // 提取所有 folder 的 children
        .filter(child => child.type === "site");  // 只选择 type 为 "site" 的项
      console.log(sites); // 打印所有找到的 site 项


    },
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
          this.jsonBookMarks = jsonBookMarks;
          
          this.processBookmarksJson(jsonBookMarks);
        })
        .catch((err) => {
          console.error("Error loading HTML file:", err);
        });
    },
    bookmarksHtmlToJson(html) {
      const $ = load(html, { decodeEntities: false });
      const root = [];

      const parseNode = (node) => {
        const eq0 = node.children().eq(0);
        const name = eq0.html() || "";
        let type = "site";
        let href = "";
        let icon = "";
        let children = [];

        if (eq0[0].name === "h3") {
          // Folder type
          type = "folder";
          const dl = node.children("dl").first();
          const dts = dl.children("dt");
          children = dts
            .toArray()
            .map((ele) => parseNode($(ele)))
            .filter((item) => item !== null);
        } else if (eq0[0].name === "a") {
          // Site type
          href = eq0.attr("href") || "";
          icon = eq0.attr("icon") || "";
        }

        return { name, type, href, icon, children };
      };

      const body = $("body");
      const rootFolder = this.getRootFolder(body);
      const rdt = rootFolder.children("dt");

      rdt.each((_, item) => {
        const node = $(item);
        const child = parseNode(node);
        root.push(child);
      });

      // 为每个文件夹项添加 open 属性

      return root;
    },
    getRootFolder(body) {
      const h3 = body.find("h3").first();

      if (typeof h3.attr("personal_toolbar_folder") === "string") {
        return body.children("dl").first(); // Chrome
      }
      if (typeof h3.attr("folded") === "string") {
        return body; // Safari
      }
      if (typeof h3.attr("item_id") === "string") {
        return body.children("dl").first(); // IE
      }
      if (h3.text() === "Mozilla Firefox") {
        return body.children("dl").first(); // Firefox
      }
      return body.children("dl").first(); // Default case
    },
  },
};
</script>
<style scoped>

</style>