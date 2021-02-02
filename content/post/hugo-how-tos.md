---
title: "Hugo How-tos"
tags: ['Hugo', 'Static Site Generators', 'JAM Stack']
date: 2021-01-19T05:23:18-05:00
draft: false
---

## How do you install Hugo?

The easiest way is to use the Chocolatey package manager if you are on Windows. If you haven't already install Chocolatey. To check if it is installed already use the following command: 

{{< cmd >}}

choco version

{{< /cmd >}}

If you do not see an error than it is installed. Otherwise navigate to the PM's website and follow the instructions.

 To install Hugo using Chocolatey use the following command: 

{{< cmd >}}

choco install hugo

{{< /cmd >}}

In addition to the usual benefits of using a PM, This has the benefit of automatically adding Hugo's location to your list of path variables. To confirm that the installation was successful, use a terminal tool (eg PowerShell) of your choice and type the following command:

{{< cmd >}}

hugo version

{{< /cmd >}}

If you see information regarding your version of Hugo then the installation should have been completed successfully.



## How do you start a new site with Hugo?

Open your desired terminal tool and navigate to the desired directory where you wish to place the new site. The use the following command:

{{< cmd >}}

hugo new site <SITENAME>

{{< /cmd >}}

This will create a new directory baring the name of your site and the skeleton site that will ultimately be converted into a HTML/CSS/JS directory that can directly be uploaded to a hosting site.



## How do you add a pre-made themes to Hugo?

A theme can be either added manually or using git. The later is easier. Utilizing this method involves first going to the git page that hosts the theme. After this you will copy the link and open your terminal tool. In the themes directory you will use the following command:

{{< cmd >}}

git clone <GITURL>

{{< /cmd >}}

From here you will navigate to your site configuration file `config.toml`. If you are adding a them for the first time you will simply append a line that says as follows:

{{< cmd >}}

theme = "<THEMENAME>"

{{< /cmd >}}

This will cause Hugo to search your themes file for this theme. 



## How do you add a new page in Hugo?

While new pages in Hugo can be added manually using command line tools or the GUI, Hugo provide a convenience operator that will automate the process. To utilize it enter the following command:

{{< cmd >}}

hugo new <POSTNAME>.md

{{< /cmd >}}



Although optional, it is perhaps a good idea to use some sort of file structure. As an example we might elect to place all of our posts in a posts directory. The above file would then become

{{< cmd >}}

hugo new posts/<POSTNAME>.md

{{< /cmd >}}



## How do you add images to a page?



## How can you activate a local server to view your site via Hugo?

{{< cmd >}}

hugo server -D

{{< /cmd >}}



## What are some useful shortcodes for Hugo







## How do I actually build the static pages?



## How do I make Hugo use relative URLs?



## How can I change my Markdown Handler and why would I want to?

 Not all markdown handlers have the same features. Blackfriday was the default used by Hugo until version 0.60 (the current is Goldmark) and was paranoid about security and so I was safe to feed hypothetical user inputs on your website directly into the renderer. The downside? As of January 2021 it doesn't allow for inline KaTeX. This contrasts with Mmark (deprecated) which is less secure but will allow for extremely easy usage of inline math demarked by double dollar signs.



## How do I support inline math in Hugo?

At the time of this writing (2021) KaTeX doesn't have inline math working out of the box. Instead it is important to navigate to the partial in your Hugo theme that makes the JS calls to activate KaTex and make some quick modifications as needed. The first is the check the version of KaTeX used by your theme. It might be the case that your theme hasn't updated to the latest in which case it might be necessary to find an updated version and call it using a CDN. Check and see if yours is equal to or higher than KaTeX 0.11.1. An example of what this might look like is included below.




<!-- Katex css -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.css" integrity="sha384-zB1R0rpPzHqg7Kpt0Aljp8JPLqbXI3bhnPWROx27a9N0Ll6ZP/+DiW/UqRcLbRjq" crossorigin="anonymous">

<!-- The loading of KaTeX is deferred to speed up page rendering -->

<script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/katex.min.js" integrity="sha384-y23I5Q6l+B6vatafAwxRu/0oK/79VlbSz7Q9aiSZUvyWYIYsd+qj+o24G5ZU2zJz" crossorigin="anonymous"></script>


<!-- To automatically render math in text elements, include the auto-render extension: -->

<script defer src="https://cdn.jsdelivr.net/npm/katex@0.11.1/dist/contrib/auto-render.min.js" integrity="sha384-kWPLUVMOks5AQFrykwIup5lo0m3iMkkHrD0uJ4H5cjeGihAutqP0yW0J6dpFiVkI"
crossorigin="anonymous"
onload='renderMathInElement(document.body);'></script




Next you will want to call a short script (after the one that call KaTeX) which will modify the delimiters. 

    document.addEventListener("DOMContentLoaded", function() {
        renderMathInElement(document.body, {
            delimiters: [
                {left: "$$", right: "$$", display: true},
                {left: "$", right: "$", display: false}
            ]
        });
    });
</script>


## How do I use block quotes?



## How to create a table of contents for a post in Hugo?



## How do I use and customize syntax highlighting?

```html
<div role="dialog" aria-labelledby="dialog-heading">
  <button aria-label="close">x</button>
  <h2 id="dialog-heading">Confirmation</h2>
  <p>Press Okay to confirm or Cancel</p>
  <button>Okay</button>
  <button>Cancel</button>
</div>
```

```python
x = range(6)
for n in x:
  print(n)
```