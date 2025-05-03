Basic personal website based forked from [here](https://github.com/henrythemes/jekyll-starter-theme)


A minimalistic Jekyll starter theme for "classic" web sites (e.g. just some web pages)


```
├── _config.yml                  # site configuration
├── _layouts
|   └── default.html             # master layout template
├── css
|   └── style.css                # styles
├── three.html                   # another sample page (in hypertext markup e.g. html)
├── two.md                       # another sample page (in markdown e.g. md)
└── index.md                     # index (start) sample page (in markdown e.g. md)
```

Becomes

```
└── _site                        # output build folder; site gets generated here
    ├── css
    |   └── style.css            # styles for pages (copied 1:1 as is)
    ├── three.html               # another sample page
    ├── two.html                 # another sample page 
    └── index.html               # index (start) sample page
```

Notes

- blogs are in the format of 'dyear-month-day-date-title.md'

- test deployment `jekyll serve -s personal-site -d personal-site/_site --watch --drafts`
