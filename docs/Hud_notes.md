# Things to change
[docs](settings.md#disqus_username)
Will need to modify the shortname and the url on disqus when settling on a name

Same goes for the contact page

Make sure all url images add .png or jpeg or whatever they are to it

# Make 2nd page just for AT blog
check home.html and copy and use the code below

<section id="grid" class="row flex-grid">
    {% for post in posts offset: offset %}
        {% if "AT Blog" in post.title %}
            <article class="box-item">
                <span class="category">
                    <a href="{{ site.baseurl }}/{{ site.categories_folder | default: 'category' }}/{{ post.category }}">
                        <span>{{ post.category }}</span>
                    </a>
                </span>
                <div class="box-body">
                    <a class="cover" href="{{ post.url | prepend: site.baseurl }}">
                        {% include loader.html %}
                        {% if post.optimized_image %}
                            <img src="/assets/img/placeholder.png" width="100%" data-url="{{ post.optimized_image }}" class="preload">
                            <noscript>
                                <img src="{{ post.optimized_image }}" width="100%">
                            </noscript>
                        {% elsif post.image %}
                            <img src="/assets/img/placeholder.png" width="100%" data-url="{{ post.image }}" class="preload">
                            <noscript>
                                <img src="{{ post.image }}" width="100%">
                            </noscript>
                        {% else %}
                            <img src="/assets/img/placeholder.png" width="100%" data-url="/assets/img/off.jpg" class="preload">
                            <noscript>
                                <img src="/assets/img/off.jpg" width="100%">
                            </noscript>
                        {% endif %}
                        {% include new-post-tag.html date=post.date %}
                        {% include read-icon.html %}
                    </a>
                    <div class="box-info">
                        <time datetime="{{ post.date | date_to_xmlschema }}" class="date">
                            {% include date.html date=post.date %}
                        </time>
                        <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">
                            <h2 class="post-title">
                                {{ post.title }}
                            </h2>
                        </a>
                        <a class="post-link" href="{{ post.url | prepend: site.baseurl }}">
                            <p class="description">{{ post.description }}</p>
                        </a>
                        <div class="tags">
                            {% for tag in post.tags %}
                                {% if tag != "" %}
                                    <a href="{{ site.baseurl}}/tags/#{{tag | slugify }}">#{{ tag }}</a>
                                {% endif %}
                            {% endfor %}
                        </div>
                    </div>
                </div>
            </article>
        {% endif %}
    {% endfor %}
</section>


