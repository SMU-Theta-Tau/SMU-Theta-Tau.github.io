# SMU-Theta-Tau.github.io
Repository for hosting the website for SMU Theta Tau Tau Beta

## Transition Guide / Dev Guide
*By Jackson Scott Reed, TB618 X! YY! VV!*

If you are the new Web Admin, welcome!

If you're an outgoing Web Admin, remember to add the new officer as a contributor on the repo!

If you have questions about the project that the previous web admin can't answer, feel free to reach out to me at (469) 859-0983.

### Project Structure

```
├── _layouts/
│   ├── default.html      # Global layout (HTML shell, header, footer)
│   └── home.html         # Homepage content layout
│
├── _includes/
│   ├── header.html       # Navigation bar (if using partials)
│   ├── footer.html       # Footer section
│   ├── hero.html         # Homepage hero banner
│   ├── aboutus.html
│   ├── slideshow.html
│   ├── calendar.html
│   ├── resources.html
│   ├── member-card.html  # Single member card component
│   └── officer-card.html # Reusable officer card component (optional)
│
├── _data/
│   ├── members.yml       # Auto-generated from CSV
│   └── officers.yml      # Optional structured officers data
│
├── assets/
│   ├── css/
│   │   └── styles.scss   # Entire site styling
│   └── js/               # (optional) custom JS
│
├── pages/
│   ├── officers.html     # Leadership page (now using default layout)
│   ├── members.html      # Auto-generated directory page
│   └── images/           # Officer photos + placeholder images
│
├── img/
│   └── members/          # Member photos named by roll number
│
├── index.md              # Homepage entry point (uses layout: home)
├── _config.yml           # Jekyll configuration
└── README.md             # This file
```

### Local Development Environment

To run the website locally:

1. Install Ruby on your machine *(Note: Must use Ruby 3.1.X or older)*
2. In the repo, install Bundler:
    ```bash 
    gem install bundler
    ```
3. Install dependencies:
    ```bash 
    bundle install
    ```
4. Serve Locally:
    ```bash
    bundle exec jekyll serve
    ```
5. Site will be available at:
    ```http://127.0.0.1:4000/```


### Members Directory

Member Data lives in ``` _data/members.yml```. You will need to update this each semester as people are initiated and members graduate. Feel free to request photos and nicknames/titles from members. The members page is automatically populated with the data from this file.

Photos (on both the member and officer pages) are loaded automatically using the pattern ``` /pages/images/<rollnumber>.jpg```. New photos must be uploaded under this format to work correctly. In order to keep the repo fairly lightweight, try to keep the images under ~500 KB. They won't be displayed very large so they don't need to be super high quality.

### Home Page

The homepage is controlled by:

```index.md``` → loads layout: home

```_layouts/home.html``` → includes hero, about, slideshow, calendar, resources

```_layouts/default.html``` → wraps everything with global page structure

This separation keeps your code clean and avoids duplication.

#### Slideshow

Slideshow images are loaded using:

```yaml
slideshow-filenames:
  - photo1
  - photo2
  - photo3
```

The include:
```{% include slideshow.html %}```
automatically builds a responsive slideshow. Be sure to update the slideshow photos every couple of months.

### Blog

Jekyll comes with blog post functionality built-in! All you have to do is add the content and it will automatically populate in the carousel and news page.

See the existing articles for the template--just copy over the top part, change the parameters accordingly, and write the article in markdown.

### Deployment

The site is deployed automatically by GitHub Pages on push.

Make sure _config.yml contains:

```yaml
markdown: kramdown
theme: null
plugins:
  - jekyll-relative-links
exclude:
  - Gemfile
  - Gemfile.lock
  - README.md
  ```

And ensure GitHub Pages is set to build from ```main / root```.
