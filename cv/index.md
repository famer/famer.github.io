---
title: CV
layout: twocolumns
type: page
permalink: /cv2/
---

{% assign cvs = site.pages | where:"type","cv" | sort:"weight" | reverse %}
{% for cv in cvs %}
* [{{ cv.title }} (printable HTML)]({{ cv.url }}) [(<i class="fa fa-file-pdf-o"></i> Pdf {{ cv.pdfSize }})](/assets/cv/{{ cv.pdf }} ) {{ cv.status }} 
{% endfor %}

Old version(mostly only workplaces):
[<i class="fa fa-file-pdf-o"></i> Pdf 107 Kb](/assets/cv/cv_-_timur_tatarshaov.pdf)
