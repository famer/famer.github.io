# Personal website for graduate/beginner IT

In this repository currently enlisted sources of actual working copy of [personal website of Timur Tatarshaov](http://timurtatarshaov.me).
Since it's hosted on GitHub Pages what you see on mantioned webpage is generated directly from this sources on the fly.

## Usage & configs

- Basic information related to site contained in [_config.yml](_config.yml)
- Top header links hardcoded in [_layouts/core.html](_layouts/core.html)
- Every page of website is generated based on markup file [_layouts/twocolumns.html](_layouts/twocolumns.html) which extends previously mentioned [core.html](_layouts/core.html) file
- Every main section pages generated from file respective_folder_name/index.md
- All the contact info used on website taken from [_data/general_data.yml](_data/general_data.yml) file in YAML format

### CVs

Process of generation of CVs a bit different from regular pages.

- CVs data taken from [_data/cv/](_data/cv/)"respective_file_name.yml". It contains all data specific dasta related to CV: description, experience, etc.  
General data, like contact info, languages, etc., is taken from _data/general_data.yml
- CVs itself generated from files from the folder [cv](cv)  
each file there, apart of index.md which just generates list of the links to CVs, contains following front matter variables  
  - title -- title of the CV. Used in list of CVs links and in CV itself   
  - dataFileName -- name of the respective data file in [_data/cv/](_data/cv/) folder in YAML format  
  - pdf -- name for respective file in PDF format for current CV, places in [assets/cv/](assets/cv/) folder
  - pdfSize -- size of mentioned PDF file with units, eg "100 Kb"
  
### Local run and development on local machine
To run this site localy you would need to have [jekyll](http://jekyllrb.com) installed.

Once installed execute `jekyll serve` in sources folder and naviage to represented url in your browser ( <http:// 127.0.0.1:4000/> by default ). 

__Current website use CDN for [Bootstrap](http://getbootstrap.com) and [FontAwesome](http://fontawesome.io/) so you would need to have internet connection to run it locally.__  

Happy using and enjoy.

### License
Everything excluding personal data released under [MIT license](LICENSE).

--
Timur Tatarshaov
<http://timurtatarshaov.me> 
