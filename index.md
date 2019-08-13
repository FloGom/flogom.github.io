---
---

<nav>
  {% for item in site.data.navigation %}
    <a href="{{ item.link }}" {% if page.url == item.link %}style="color: red;"{% endif %}>
      {{ item.name }}
    </a>
  {% endfor %}
</nav>

# Fun and Useless Projects - F.a.U.P
## An attempt to help humanity reducing boredom...

Here are my tries at open-source alternatives, and DIY project to save 
humanity from boredom!

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{post.date}} - {{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

It is also a notebook for projects.

### Table of Content
Content is broken down in several categories:    
[01. Old Computers](01_OldComputers/index_01.md)    
[02. Engineering]()    
[03. Misc]()    

Have fun !

Flogom

Fun Logically Organised Games and Operating Modules.
Fun Logical Organised Graphics Operational Methods.

### Contact