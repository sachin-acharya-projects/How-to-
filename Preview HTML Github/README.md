# How to RENDER HTML directly from github
___________________________________________

* Method 1 [https://htmlpreview.github.io/?url]  

    We can just append our github path in-place of <url> and all done
    Example:
    ````python
    https://htmlpreview.github.io/?https://github.com/sachin-acharya-projects/AnalogClock/main/index.html

    # https://github.com/sachin-acharya-projects/AnalogClock/main/index.html is my path to index.html in main
    # branch of AnalogClock Repository

    # Only possible with public repositories
    ````

* Method 2 [Using Github Pages](https://pages.github.com/)
    More details in the page

## Github as CDN
You can also use GitHub as CDN

````
 https://cdn.jsdelivr.net/gh/{username}/{repo}/
````
Just need to replace {username} with your github-username and {repo} with your repo along with path to file

Exampe:
````python
https://cdn.jsdelivr.net/gh/sachin-acharya-projects/AnalogClock/clock.js

# Using Above repo as CDN to host clock.js file
````

[Source](https://github.com/jsdelivr/jsdelivr)
