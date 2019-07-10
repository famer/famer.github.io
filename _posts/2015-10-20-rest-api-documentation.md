---
title: REST API Documentation
---
REST docs vs swagger, editor, ui, codepen generation schemes

Comparison  
Ok, so you are probably wrote your REST API service properly designed and next thing you want is to develop documentation for it since it has to be used by other people and services.

I got such a task and decided to perform investigation of tool to choose for that purposes.

So criterias were: better results with less effort, easiness to design and describe(develop), pleasant look of final documentation, ability to generate static HTML files, ability to live check and perform queries, "live" tool, meaning strong development community behind it which means it will support new approaches and fix bugs.

Candidates:  
<https://apiblueprint.org/> special format based on Markdown, all other tools are external and quite spread. Quite open.

<http://projects.spring.io/spring-restdocs/> Spring REST Docs. Requeres much of manual work, so basically automatically generates snippets based on unit tests written in a special way. Snippets could be used after in a documentation as excerpts.  
Tests fails if there is not special addition of it to generate the snippet. Official Spring project, quite flexible due to manual work. No designer, no live testing so far but it's quite new.

Swagger. Has several sub tools. Swagger editor allows to design describe and design API based on yaml format, which interpreted to pretty looking docs. Useful part is possibility to describe the model and use it as description of expected and produced objects. To generate the docs swagger codegen could be used, it has several output formats starting from basic HTML, clients for several languages and ending up nodejs app.  
Swagger UI, just accepts yaml file from Swagger Editor and displays docs using JavaScript. It's not static at the end and do not have good online API testing tool, which is actually in editor.  
Project has quite strong community of developers behind it and quite live.  
But unfortunately so far is not able to generate static HTML pages that could test API in good way. Has been chosen due to abundance of tools and active development.

<https://github.com/mikekelly/hal-browser> since Spring Data Rest produces json+special links and description(hal) there is a tool that could be used to explore resulting API. Hal browser does exactly it. Not enought for good documnetation but for explorations quite good.

<https://www.npmjs.com/package/swagger-to-html> swagger-to-html quite simple and good looking generator, that produces only html pages without posisbility to live test API, uses bootstrap to improve appearance.
