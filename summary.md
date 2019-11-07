---
permalink: /my/permalink/summary
---

---
# Content
---

---
## pages 챕터
---

루트 폴더에 파일 추가 (index.html, about.html 등등)

index.html의 주소는 /
about.html의 주소는 /about.html

md확장자 파일도 html으로 변환 (그러나 비어있는 Front Matter 선언이라도 해야 함)
https://stackoverflow.com/questions/29662793/using-liquid-tags-in-a-jekyll-page-not-working

서브 폴더만들고 page 삽입 가능
ex) sub/page.html 주소는 /sub/page.html

_sites 폴더에 만들어짐

---
## posts 챕터
---

_posts 폴더 만들고 내부에 파일 추가

ex) 2019-11-01-hello-world.md

마크다운 파일은 html로 변환됨 (반드시 front matter로 시작)

루트 폴더에 assets 폴더(이름은 아무거나 가능) 만들고 필요한 이미지, 리소스 저장 가능

```
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
```

liquid 템플릿 문법 사용 가능

---
## Front Matter
---

```
---
layout: post
title: Blogging Like a Hacker
---
```

permalink : URL 직접 정하기(기본은 /year/month/day/title.html)
published : true or false (올릴지 말지 여부)

그냥 쓸 수 있는 변수 (date, categories, tags)

직접 변수 지정도 가능

---
## Data Files
---

_data 폴더 내부에 데이터 파일 추가

YAML, JSON, CSV 데이터 활용 가능

파일 이름이 변수이름 처럼 활용

**_data/persons.json**
```
[
	{"name":"John", "age":20},
	{"name":"Jane", "age":30},
]
```

```
<ul>
{% for p in site.data.persons %}
  <li>{{ p.name }}, {{ p.age }}</li>
{% endfor %}
</ul>
```

---
## Static Files
---

A static file is a file that does not contain any front matter. These include images, PDFs, and other un-rendered content.

https://kgmyh.github.io/blog/2017/12/23/Jekyll_Using_Sass/

SASS 사용하기

---
# SITE STRUCTURE
---

---
## Includes
---

Passing parameters to includes 가능

```
{% raw %}
<div markdown="span" class="alert alert-info" role="alert">
<i class="fa fa-info-circle"></i> <b>Note:</b>
{{ include.content }}
</div>
{% endraw %}
```

```
{% raw %}
{% include note.html content="This is my sample note." %}
{% endraw %}
```

```
{% raw %}
<figure>
   <a href="{{ include.url }}">
   <img src="{{ include.file }}" style="max-width: {{ include.max-width }};"
      alt="{{ include.alt }}"/>
   </a>
   <figcaption>{{ include.caption }}</figcaption>
</figure>
{% endraw %}
```

```
{% raw %}
{% include image.html url="http://jekyllrb.com"
max-width="200px" file="logo.png" alt="Jekyll logo"
caption="This is the Jekyll logo." %}
{% endraw %}
```

---
## Layouts
---

---
## Permalinks
---

Front Matter에 특정 주소 퍼마링크 설정 가능

글로벌 퍼마링크 양식 지정 가능

