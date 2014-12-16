Pico Search Plugin
====
Provides very basic search functionality, loosely ranking results based on number of matches per page. To be improved for better search results.
## Usage
1. Create a page with any name you like, for example "search". In the meta section include `Purpose: search_results`.
2. In your template provide a basic HTML form with an input field named `q`, method GET, and action URL pointing to the page you have created.
3. Add the following code to your template near the {{ content }} tag:
```twig
{% if meta.purpose == "search_results" and search_results %}
        {% for page in search_results %}
                <h4><a href="{{ page.url }}">{{ page.title }}</a></h4>
                {% if page.date %}<p class="meta">{{ page.date_formatted }} by {{ page.author }}</p>{% endif %}
                <p class="excerpt">{{ page.excerpt }}</p>
        {% endfor %}
{% endif %}
```