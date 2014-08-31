---
layout: home
---

<div class="index-content mess">
    <div class="section">
        <ul class="artical-cate">
            <li><a href="/"><span>Blog</span></a></li>
            <li class="on" style="text-align:center"><a href="/mess"><span>mess</span></a></li>
            <li><a href="/leetcode"><span>Leetcode</span></a></li>
        </ul>

        <div class="cate-bar"><span id="cateBar">mess</span></div>

        <ul class="artical-list">
        {% for post in site.categories.mess %}
            <li>
                <h2>
                    <a href="{{ post.url }}">{{ post.title }}</a>
                </h2>
                <div class="title-desc">{{ post.description }}</div>
            </li>
        {% endfor %}
        </ul>
    </div>
    <div class="aside">
    </div>
</div>
