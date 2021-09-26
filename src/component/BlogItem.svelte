<script lang="ts">
    import dayjs from 'dayjs'

    import type { Blog } from './type'
    export let blog: Blog
</script>

<main>
    <div class="blog__title">{blog.title}</div>

    <ul class="blog-item__categories">
        {#each blog.categories as category}
            <li>
                {category}
            </li>
        {/each}
        </ul>
    <div class="blog-item__date">{ dayjs(blog.pubDate).format("MMMM D, YYYY")}</div>
</main>

<style> 
    main {
        background-color: #444444;
        width: 100%;
        border-radius: 2px;
        padding :1rem;
        transition: transform .2s; /* Animation */
    }

    main:hover{
        transform: scale(1.05);
    }

    .blog__title {
        font-size: 1rem;
        line-height: 1.5rem;
    }

    ul {
        display: flex;
        flex-wrap: wrap;
        padding: 0;
        list-style-type: none;
        margin-left: -0.5rem;
        margin-bottom: 0.5rem;
    }

    ul > li {
        margin-left: 0.25rem;
        margin-top: 0.25rem;
        font-weight: 300;
        background-color: #727272;
        padding: 0.25rem 0.5rem;
        border-radius: 4px;
        font-size: 0.75rem;
        white-space: nowrap;
    }
    

    .blog-item__date{
        margin-top: 1rem;
        font-weight: 100;
        font-size: 0.75rem;
        line-height: 1.5rem;
    }
</style>