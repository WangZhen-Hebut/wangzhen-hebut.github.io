<h2 id="publications" style="margin: 2px 0px -15px;">Publications</h2>

<div class="publications">
<ol class="bibliography">

{% assign papers = site.data.publications.main | sort: "published" | reverse %}
{% assign shown = 0 %}
{% for link in papers %}
{% unless site.homepage_ranks contains link.rank %}{% continue %}{% endunless %}

<li id="paper-{{ link.id }}">
<div class="pub-row">
  <div class="col-sm-3 abbr" style="position: relative;padding-right: 15px;padding-left: 15px;">
    {% if link.image %} 
    <a href="{{ link.image }}" aria-label="View figure for {{ link.title | escape }}"><img src="{{ link.image }}" alt="{{ link.figure_caption | default: link.title | escape }}" class="teaser img-fluid z-depth-1" style="object-fit:contain;background:white;"></a>
    {% endif %}
    {% if link.conference_short %} 
    <abbr class="badge">{{ link.conference_short | escape }}</abbr>
    {% endif %}
  </div>
  <div class="col-sm-9" style="position: relative;padding-right: 15px;padding-left: 20px;">
      <div class="title"><a href="{{ link.url }}">{{ link.title | escape }}</a></div>
      <div class="author">{{ link.authors }}</div>
      <div class="periodical"><em>{{ link.conference }}</em>
      </div>
    <div class="links">
      {% if link.pdf %} 
      <a href="{{ link.pdf }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">PDF</a>
      {% else %}
      <a href="{{ link.url }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">DOI</a>
      {% endif %}
      {% if link.code %} 
      <a href="{{ link.code }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">Code</a>
      {% endif %}
      {% if link.page %} 
      <a href="{{ link.page }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">Project Page</a>
      {% endif %}
      {% if link.bibtex %} 
      <a href="{{ link.bibtex }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;">BibTex</a>
      {% endif %}
      {% if link.notes %} 
      <strong> <i style="color:#e74d3c">{{ link.notes }}</i></strong>
      {% endif %}
      {% if link.others %} 
      {{ link.others }}
      {% endif %}
    </div>
  </div>
</div>
</li>

<br>

{% assign shown = shown | plus: 1 %}
{% if shown == 6 %}{% break %}{% endif %}
{% endfor %}

</ol>
</div>

