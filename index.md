# 这里是我的个人介绍
## 我有两个项目想要展示
Regression Model 

[智能计价回归模型](<https://github.com/Yvette-YL/TaxiFareEstimatior/blob/main/README.md> "")

Machine Learning Model
<h1>如果在这里直接展示所有post呢？</h1>

<ul>
  {% for post in site.posts %}
    <li>
      <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
      <p>{{ post.excerpt }}</p>
    </li>
  {% endfor %}
</ul>
