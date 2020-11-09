---
layout: home
permalink: /index.html
---

{% include kindle.html %}

<hr>

## [Blog](/blog)
<div class="posts">
  <ul>
  {% for post in site.categories.blog | limit: 3 %}
    <li><a href="{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
    </ul>
</div>

<hr>

## [Journal](/journal)
<div class="posts">
  {% for post in site.categories.journal | limit: 1 %}
   <article class="post">
    <strong><time datetime="{{ post.date | date_to_xmlschema }}" class="post-date">{{ post.date | date: "%A, %B %d, %Y" }}</time></strong>
    {{ post.content }}
   </article>
  {% endfor %}
</div>

<hr>

## [Videos](/videos)
{% for post in site.categories.video limit:1 %}
  <div class="video">
  	{% assign foundiFrame = 0 %}
	{% assign iFrames = post.content | split:"<iframe " %}
	{% for iFrame in iFrames %}
		{% if iFrame contains 'src' %}
			{% if foundiFrame == 0 %}
				{% assign html = iFrame | split:">" | first %}
				<iframe {{ html }}></iframe>
				{% assign foundiFrame = 1 %}
			{% endif %}
		{% endif %}
	{% endfor %}
  </div>
{% endfor %}

<hr>

## [Photos](/photos)
<div class="grid">
  {% for post in site.categories.photos | limit: 4 %}
	  <div class="gridBox">
	  	<a href="{{ post.url }}">
	  	{% assign foundImage = 0 %}
	  	{% assign images = post.content | split:"<img " %}
	  	{% for image in images %}
	    	{% if image contains 'src' %}
	        	{% if foundImage == 0 %}
	            	{% assign html = image | split:"/>" | first %}
	            	<img {{ html }} />
	            	{% assign foundImage = 1 %}
	        	{% endif %}
	    	{% endif %}
	  	{% endfor %}
	  	<span class="boxText">{{ post.title }}</span></a>
	  </div>
  {% endfor %}
</div>

<hr>

## [Music](/music)
<div class="grid">
  {% for post in site.tags["albums"] | limit: 4 %}
	  <div class="gridBox">
	  	<a href="{{ post.url }}">
	  	{% assign foundImage = 0 %}
	  	{% assign images = post.content | split:"<img " %}
	  	{% for image in images %}
	    	{% if image contains 'src' %}
	        	{% if foundImage == 0 %}
	            	{% assign html = image | split:"/>" | first %}
	            	<img {{ html }} />
	            	{% assign foundImage = 1 %}
	        	{% endif %}
	    	{% endif %}
	  	{% endfor %}
		</a>
	  </div>
  {% endfor %}
</div>

<hr>

## [Shop](/shop)
<div class="grid">
  {% for post in site.categories.shop | limit: 4 %}
	  <div class="gridBox">
	  	<a href="{{ post.url }}">
	  	{% assign foundImage = 0 %}
	  	{% assign images = post.content | split:"<img " %}
	  	{% for image in images %}
	    	{% if image contains 'src' %}
	        	{% if foundImage == 0 %}
	            	{% assign html = image | split:"/>" | first %}
	            	<img {{ html }} />
	            	{% assign foundImage = 1 %}
	        	{% endif %}
	    	{% endif %}
	  	{% endfor %}
	  	</a>
	  </div>
  {% endfor %}
</div>