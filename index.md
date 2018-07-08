<section id="more-work">
    {% if page.previous %}
        {% assign previous = page.previous %}
    {% else %}
        {% assign previous = site.posts[0] %}
    {% endif %}
    <div class="left">
        <a class="equalize" href="{{site.baseurl}}{{previous.url}}" title="Previous Post: {{previous.title}}">
            <div>
                <h6> ← Previous Project </h6>
                <h4> {{previous.title}} </h4>
            </div>
        </a>
    </div>

    {% if page.next %}
        {% assign next = page.next %}
    {% else %}
        {%comment%}
           As the array index start at zero we substract 1 to the total count,
           we then get the last post index in the site.posts array
        {%endcomment%}
        {% assign last lastPostIndex = site.posts | size | minus: 1 %}
        {% assign next = site.posts[lastPostIndex] %}
    {% endif %}
    <div class="right">
        <a class="equalize" href="{{site.baseurl}}{{next.url}}" title="next Post: {{next.title}}">
            <div>
                <h6> Next Project →</h6>
                <h4> {{next.title}}</h4>
            </div>
        </a>
    </div>
</section>