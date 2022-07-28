<template>
  <Layout>
    <!-- Learn how to use images here: https://gridsome.org/docs/images -->

    <p>
      {{ $page.allContentfulBlogpost.edges[0].node.title }}
    </p>

    <p>
      {{ $page.allContentfulBlogpost.edges[0].node.location }}
    </p>

    <p>
      {{ $page.allContentfulBlogpost.edges[0].node.listeningTo }}
    </p>

    <hr />

    <p>
      {{ richtextToHtml($page.allContentfulBlogpost.edges[0].node.blogBody) }}
    </p>
  </Layout>
</template>

<page-query>
query Blank {
  allContentfulBlogpost {
    edges {
      node {
        title
        location
        listeningTo
        blogBody
      }
    }
  }
}
</page-query>

<script>
import { Pager } from "gridsome";

import { documentToHtmlString } from "@contentful/rich-text-html-renderer";

export default {
  metaInfo: {
    title: "Hello, world!",
  },
  components: {
    Pager,
  },
  methods: {
    richtextToHtml(content) {
      return documentToHtmlString(content);
    },
  },
};
</script>

<style>
.home-links a {
  margin-right: 1rem;
}
</style>
