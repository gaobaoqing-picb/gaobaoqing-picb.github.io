## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/gaobaoqing-picb/gaobaoqing-picb.github.io/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/gaobaoqing-picb/gaobaoqing-picb.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.


{% extends "base.html" %} 

{% block assets %}
{{ super() }}
<link rel="stylesheet" href="{{ url_for('static', filename='css/components/slideshow.almost-flat.min.css') }}" type="text/css">
<link rel="stylesheet" href="{{ url_for('static', filename='css/components/slidenav.almost-flat.min.css') }}" type="text/css">
<script src="{{ url_for('static', filename='js/components/slideshow.min.js') }}" type="text/javascript" charset="utf-8"></script>
{% endblock assets %}

{% block content %}

<div>
    <div style="float:left;width:58.7%;" >
        <div class="uk-slidenav-position uk-margin-top uk-margin-bottom" data-uk-slideshow="{kenburns:true, autoplay:true}">
            <ul class="uk-slideshow">
                {% for picture in pictures %}
                <li><img src="{{ url_for('static', filename='image/pictures/' + picture) }}" alt="picture" width="800" height="400"></li>
                {% endfor %}
            </ul>
            <a href="#" class="uk-slidenav uk-slidenav-contrast uk-slidenav-previous" data-uk-slideshow-item="previous" style="color: rgba(255,255,255,0.4)"></a>
            <a href="#" class="uk-slidenav uk-slidenav-contrast uk-slidenav-next" data-uk-slideshow-item="next" style="color: rgba(255,255,255,0.4)"></a>
        </div>
    </div>
    <div style="float:left;width:38%;margin:14px 0 0 35px;">
        <!--    <div class="uk-width-medium-3-5">.  -->
            <div class="uk-panel uk-panel-box uk-panel-box-secondary uk-panel-header" style="height:302px;overflow-y:auto;">    <!--style="height: 520px;"  -->
                <h2 class="uk-panel-title">News</h2>
                <ul class="uk-list-space uk-vertical-align-top">
                    {% for entry in news %}
                    <li>
                        <p class="uk-article-lead"><em class="uk-text-danger">{{ entry.year }} {{ entry.month }}</em>: {{ entry.content|strong|safe }}</p>
                    </li>
                    {% endfor %}
                </ul>
                <a class="uk-button-link uk-align-right uk-text-large" href="{{ url_for('news') }}" type="button">More</a>
            </div>
       <!--   </div>   -->

    </div>
</div>


<div style="clear:left;height:50px"></div>

<div class="uk-grid" data-uk-grid-margin>

    <div class="uk-width-medium-3-5">
        <div class="uk-panel uk-panel-box uk-panel-box-secondary uk-panel-header" style="height:590px;">
            <h2 class="uk-panel-title">Research</h2>
            <div class="uk-width-1-1">
                {{ research.content|markdown }}
            </div>
            <!-- <a class="uk-button-link uk-align-right uk-text-large" href="{{ url_for('news') }}" type="button">More</a> -->
        </div>
    </div>

    <div class="uk-width-medium-2-5">

        <div class="uk-panel uk-panel-box uk-panel-box uk-panel-box-secondary uk-panel-header">
            <h2 class="uk-panel-title">Collaborators & Supports</h2> 
            {% for collaborator in collaborators %}
            <p><a class="uk-link-muted" href="{{ collaborator.link }}"><i class="uk-icon-user"></i> {{ collaborator.info }}</a></p>
            {% endfor %}
            {% for support in supports %}
            <p><a class="uk-link-muted" href="{{ support.link }}"><i class="uk-icon-institution"></i> {{ support.info }}</a></p>
            {% endfor %}
        </div>

        <div class="uk-panel uk-panel-box uk-panel-box uk-panel-box-secondary uk-panel-header" style="margin-top: 18px">
            <h2 class="uk-panel-title">Links</h2>
            {% for link in links %}
            <p><a class="uk-link-muted" href="{{ link.link }}"><i class="uk-icon-link"></i> {{ link.info }}</a></p>
            {% endfor %}
        </div>

        <div class="uk-panel uk-panel-box uk-panel-box uk-panel-box-secondary uk-panel-header" style="margin-top: 18px">
            <h2 class="uk-panel-title">Contact</h2>
            <p><i class="uk-icon-street-view"></i> Address: {{ contact.address }}</p>
            <p><i class="uk-icon-phone"></i> Telephone: {{ contact.telephone }}</p>
            <p><i class="uk-icon-envelope"></i> Email: {{ contact.email }}</p>
        </div>

    </div>
    
</div>


{% endblock content %}

{% block body_footer %}
<hr class="uk-grid-divider">
<div class="uk-panel uk-text-center">
    <script type="text/javascript" src="//rc.revolvermaps.com/0/0/3.js?i=2lkeqnxkw2h&amp;b=0&amp;s=30&amp;m=2&amp;cl=ffffff&amp;co=010020&amp;cd=aa0000&amp;v0=60&amp;v1=60&amp;r=1" async="async"></script>
    <p>Powered by <a href="http://getuikit.com">UIKit</a> and <a href="http://flask.pocoo.org">Flask</a>.</p>
    <p>Copyright 2012-2018 Eukaryotic Transcriptomics (Yang Lab). All rights reserved.</p>
</div>
{% endblock body_footer %}




