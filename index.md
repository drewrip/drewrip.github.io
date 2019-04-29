---
layout: default
---

<div style="padding-top: 5vh"></div>

Hi! My name is Drew and I am a high school junior from Cincinnati, Ohio, interested in CS.

Here you can find my résumé, or my blog where I a writting about stuff I am working on.

I also have all my projects on [GitHub](https://github.com/drewrip) if you are looking for any of my work.

<div class="home">
{% for post in site.posts%}
  <div class="post postContent">
    <div  class="postDate"><time datetime="{{ post.date | date_to_xmlschema }}" itemprop="datePublished">{{ post.date | date: "%b %-d, %Y" }}</time>
    </div>
    <div class="postTag">
      {{post.tag}}
    </div>
    <br>
    <div class="postTitle">
    <a class='postLink' href="{{site.url}}{{site.baseurl}}{{post.url}}">{{post.title}}</a>
    </div>
    <div class="postExt">
   {{ post.content | strip_html | truncate:200}}
    </div>
  </div>

  {% endfor %}
  {% if site.total_pages > 1 %}
    <nav class="pagination">
      {% if paginator.previous_page %}
        <a class="paginationLink" href="{{ paginator.previous_page_path | prepend: site.baseurl | replace: '//', '/' }}">&laquo; Prev</a>
      {% endif %}

    {% for page in (1..paginator.total_pages) %}
      {% if page == paginator.page %}
        <em class="paginationLink paginationLinkCurrent">{{ page }}</em>
      {% elsif page == 1 %}
        <a class="paginationLink" href="/">{{ page }}</a>
      {% else %}
        <a class="paginationLink" href="{{ site.paginate_path | prepend: site.baseurl | replace: '//', '/' | replace: ':num', page }}">{{ page }}</a>
      {% endif %}
    {% endfor %}

    {% if paginator.next_page %}
      <a class="paginationLink" href="{{ paginator.next_page_path | prepend: site.baseurl | replace: '//', '/' }}">Next &raquo;</a>
    {% endif %}
    </nav>
  {% endif %}

</div>
