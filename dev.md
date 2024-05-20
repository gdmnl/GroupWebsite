
## Repo link:
https://github.com/gdmnl/GroupWebsite

Github account: scsegroup

Password: jonbab-kuKsy0-nizhyx

## Netlify link:
https://app.netlify.com/sites/profound-crumble-315e75/overview

(Where you can manage the update from github repo to website)

Github account: scsegroup001@outlook.com

Password: jonbab-kuKsy0-nizhyx

## To start with

run `git clone git@github.com:gdmnl/GroupWebsite.git` to clone the website code.

run `Hugo -F server` in command line under code dir to start a local server and visit `http://localhost:1313/` to see surrent local version in browser. After saving any changes in code, website page will auto refresh and show latest appearence.

run `git add .` `git commit -m "your message"` `git push` to push your changes to github repo. When successfully merged into master branch, a deploy will be triggered on netlify platform automatically and then contents on [siqiangluo.com](https://siqiangluo.com) will be same as that in repo.

Most website pages refer to a html file in /content/en/xx.html, with directly written tags and styles. Here is a simple map:

        index page:             /layouts/index.html 
        member page:            /contents/en/members.html
        selected pubs:          /contents/en/papers.html
        graph algorithm pubs:   /contents/en/graph.html
        index design pubs:      /contents/en/index_design.html
        (not shown now) other types of data management: /contents/en/otdm.html
        research interest:      /contents/en/research_interest.html
        services:               /contents/en/services.html
        recruitment:            /contents/en/recruitment.html

## Steps to add a new peper

1. each paper is represented by a 'section tag'. 

    Add a new 'section' tag in top part of paper.html. You can directly copy and paste the structure of the current latest peper and change its title, author and conference name. 

    Make sure Prof Luo's name is included by `<b> </b>` for thicker font.

    A typical 'section' should look like this, with title, authors, conference name, links to paper and code (selective):

    ```html
    <section class="slice slice-sm">
    <div class="container">
        <h4>Proteus: A Self-Designing Range Filter.</h4>
        <p class="paper-plain"> Eric Knorr*, Baptiste Lemaire*, Andrew Lim*, <b>Siqiang Luo</b>, Huanchen Zhang, Stratos Idreos, Michael Mitzenmacher. (* Equal Contribution) </p>
        <p class="paper-plain">In <b>SIGMOD 2022</b>.    
            [<a href="https://arxiv.org/pdf/2207.01503.pdf" target="_blank">Paper</a>]
            [<a href="https://github.com/Eric-R-Knorr/Proteus" target="_blank">Code</a>]
        </p> 
    </div>
</section>


2. put this 'section' tag in the correct year correponding to the conference, create a year title similar to existing ones if necessary. (2024 already created)

3. copy and paste the new 'section' to graph.html or index_design.html if it also belong to either of them. (styles are already uniformed so just copy html 'section' part)

4. copy and paste the new 'section' to research_interest.html under the correct title (graph or index). Make sure to delete one of the earlier paper to make keep only 3 papers shown in each title.

5. run `Hugo -F server` in command line to start a local server and visit `http://localhost:1313/` to test whether new changes work.

## Steps to add members

In member pages each 'section' tag contains two members because it means two members take a line in wider screen. When adding a new member, one either fill it in the last section if there is only one member in it now or create a new section if there are already two.

This is how a common member section look like, containing name, photo(now shown now) and personal info. There is a optional link to their personal page in `href` of the first `<a>` tag which means clicking anywhere of the card will redirect to a external page. `target="_blank"` means opening up a new window when redirecting.

```html
<section class="slice slice-sm collapse show" id="collapsePhD">
  <div class="container">
    <div class="row row-grid">
      <div class="col-lg-6">
        <div class="d-flex align-items-start">
          <a href="https://dblp.org/pid/305/0642.html" target="_blank" class="height_ctrl list-group-item list-group-item-action d-flex flex-column flex-md-row align-items-center  text-center text-md-left box-shadow-2">
            <div class="mr-md-sm mb-4 mb-md-0">
              <!-- <img alt="Let's Encrypt" src="/images/MoDingheng.png" width="100" height="100" class="img-fluid" /> -->
            </div>
            <div class="list-group-content">
              <div class="h5" style="color: #3771c8;">Mo Dingheng</div>
              <p>Joined in Aug 2021</p>
              <p>BS from University of Science and Technology of China​​</p>
            </div>
          </a>
        </div>
      </div>
      <div class="col-lg-6">
        <div class="d-flex align-items-start">
          <a href="https://dblp.org/pid/274/2346.html" target="_blank" class="height_ctrl list-group-item list-group-item-action d-flex flex-column flex-md-row align-items-center  text-center text-md-left box-shadow-2">
            <div class="mr-md-sm mb-4 mb-md-0">
              <!-- <img alt="Let's Encrypt" src="/images/LiaoNingyi.jpeg" width="100" height="100" class="img-fluid" /> -->
            </div>
            <div class="list-group-content">
              <div class="h5" style="color: #3771c8;">Liao Ningyi</div>
              <p>Joined in Aug 2021</p>
              <p>BS from Shanghai Jiao Tong University​</p>
            </div>
          </a>
        </div>
      </div>
    </div>
  </div>
</section>
```

In each section tag, A 'tag id' is used to show and hide people in different types, such as 'collapsePhD' should be declared for phd members. See `id="collapsePhD"` in the first line of section. This id is linked to `data-target="#collapsePhD"` in phd part title, which controls hiding or showing phd members. 

When giving the title block a click in the web page, all sections with corresponding id will change its visibility. When adding a new section or moving members into past members, do remember check its id. (or simply copy and paste from the earlier one under the same part then change infomation)


## Others:

1. About files on the server:
    * There are paper pdf file and member photo files (not shown now) stored on server, they are in /static/ dir. To add new ones, just put the file in /static/ and refer to them from '/static' (not included). For example '/docs/xxx.pdf'
    * As a github repo, file size limit corresponds with github (100M) 

5. Other tips:
    * Check for both wider screen mode and phone mode using `F12` and `ctrl+shift+M` after adding new contents because this website is auto-adaptive
