<script lang="ts">
    import { MarkdownRenderer } from "obsidian";

    import { getContext } from "svelte";
    import type StatBlockRenderer from "../statblock";

    export let property: string;
    property = property
        .replace(/<STATBLOCK-LINK>/g, "[[")
        .replace(/<\/STATBLOCK-LINK>/g, "]]");

    const context = getContext<string>("context");
    const renderer = getContext<StatBlockRenderer>("renderer");

    const markdown = (node: HTMLElement) => {
        MarkdownRenderer.renderMarkdown(property, node, context, renderer);
    };
</script>

<div class="statblock-markdown" use:markdown />

<style>
    .statblock-markdown {
        display: inline;
    }
    .statblock-markdown :global(p) {
        display: inline;
    }
</style>
