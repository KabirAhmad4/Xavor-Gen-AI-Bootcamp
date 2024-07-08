<div align='center'>

<img src=https://github.com/KabirAhmad4/Xavor-Gen-AI-Bootcamp/blob/main/Slides/titlr.png
 alt="logo"  />


<h1>Generative AI Tasks</h1>
<p>Mainly Focus on Generative AI project + Tasks related with Gen AI techniques</p>

<h4> <span> · </span> <a href="https://github.com/KabirAhmad4/Xavor-Gen-AI-Bootcamp/blob/master/README.md"> Documentation </a> <span> · </span> <a href="https://github.com/KabirAhmad4/Xavor-Gen-AI-Bootcamp/issues"> Report Bug </a> <span> · </span> <a href="https://github.com/KabirAhmad4/Xavor-Gen-AI-Bootcamp/issues"> Request Feature </a> </h4>


</div>

# :notebook_with_decorative_cover: Table of Contents

- [About the Project](#star2-about-the-project)


## :star2: About the Project

### :camera: Screenshots
<div align="center"> <a href=""><img src="https://github.com/KabirAhmad4/Xavor-Gen-AI-Bootcamp/blob/main/Flow%20Daigrams/Methodology.png" alt='image' width='500'height='650' /></a> </div>
<div align="center"> <a href=""><img src="https://github.com/KabirAhmad4/Xavor-Gen-AI-Bootcamp/blob/main/Flow%20Daigrams/Project%20Flow%20Daigram.png" alt='image' width='800'/></a> </div>


on:
  schedule:
    - cron: '0 * * * *' # Runs every hour
  push:
    branches:
      - main

jobs:
  update-readme:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout repository
      uses: actions/checkout@v2

    - name: Fetch latest commits
      run: |
        git log -5 --pretty=format:"%h - %s (%ci)" --abbrev-commit > latest_commits.txt

    - name: Update README
      run: |
        sed -i '/## Latest Commits/ r latest_commits.txt' README.md

    - name: Commit changes
      run: |
        git config --global user.name 'github-actions[bot]'
        git config --global user.email 'github-actions[bot]@users.noreply.github.com'
        git add README.md
        git commit -m 'Update README with latest commits'
        git push
