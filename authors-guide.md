---
layout: default
title: Author's Guide
---

## tl;dr: Look at Other Recipes, and Blend In

Look at the source of other recipe pages and follow that page structure. Start with the [Developer's Guide]({{ site.baseurl }}/developers-guide) to get a test version of the cookbook up and running on your machine, and get to work!

## General Guidelines

* Feel free to add new pages, or even chapters. Just keep them organized. _(See "How to Add a Chapter" below)_
* Try to stay within the Problem/Solution/Discussion format. If you can't think of a good problem for your recipe... hang onto it for a while.
* Sharing code that you think might only be used rarely is fine. Sharing esoteric code tricks is less so. There's a difference between sharing a translator for an obscure format and sharing a weird bit-shifting trick that does fast but inaccurate multiplication.
* Don't forget to add your name to the authors page!

## Use Cookbook Problem/Solution/Discussion Format

A typical cookbook page will have three sections (four if you count the title):

* **Problem** A one- or two-sentence description of the problem, such as "You want to access parts of a string" or "You want to format a floating point number as currency, with a leading dollar sign, two digits of precision and comma-separated triples." Where possible, phrase the problem as though speaking directly to the reader: "You want to...", "You have an X but you want a Y", etc.
* **Solution** State the solution as briefly as possible, ideally as a single sentence that identifies the strategy you would use, and give example code. It's tempting to explain the solution, but don't do it yet. Remember that the reader will look this solution up many times after the first time, and that they will be looking for a quick reference each time. You're going to explain the solution in the **Discussion**, and the first time reader will read your solution, think about it, and then proceed to the discussion if necessary. For example, for "accessing parts of a string", a good Solution sentence might be "Use CoffeeScript's array range subscripts, or JavaScript's slice function."
* **Discussion** Here you should explain why your solution works, or give further examples such as edge cases. If your solution can break on some edge cases, be sure to note them here. For example, if a percentage function crashes when given a zero, you could note this in the discussion and give a workaround. NOTE: If your solution has really dangerous edge cases, so dangerous that you would include them in the solution, please consider whether your recipe should be included at all. Remember, this Cookbook is for good code!

## Copyright Issues

Do not post code that is copyrighted by another user, unless you have permission to use that code AND to relicense that code under the [CC BY 3.0]({{ site.baseurl }}/license) license. If you DO have permission and the author would like credit, please show respect to them, they deserve it.

## Tag the page with Jekyll frontmatter

...that's a lot of fancy words that mean "don't forget to put the layout, chapter and page title at the top of the file in a YAML block". For example, the string interpolation page begins with

{% highlight text %}
---
layout: default
title: String Interpolation
chapter: Intrroduction
---
{% endhighlight %}

## Use Liquid highlighting templates

Turn on syntax highlighting for CoffeeScript with ` highlight go `.

{% highlight text %}
&lbrace;% highlight go %&rbrace;
&#35; Calculate the square of a number
square = (x) -> x * x

square(16)
&#35; => 256
&lbrace;% endhighlight %&rbrace;
{% endhighlight %}

This produces the following:

{% highlight coffeescript %}
# Calculate the square of a number
square = (x) -> x * x

square(16)
# => 256
{% endhighlight %}

p.s. Include inline comments

# Grindy HOWTOs

## How to Add a Recipe

Create a new markdown page (template below). The filename should be about the problem, e.g. `finding-last-day-of-the-month.md` or `reversing-arrays.md`. In your file, start with the following template:

{% highlight text %}
---
layout: default
title: Title of The Recipe
chapter: Chapter Name
---

## Problem

You have a problem.

## Solution

Do this about it.

## Discussion

Here's why.
{% endhighlight %}

One fussy little bit, the chapter name should match the directory the chapter is in, otherwise the page won't render correctly. For example, if you're writing a recipe for arrays, make sure the chapter is "Arrays", not "arrays" or "aray" ...or especially not "Chapter Name".

## How to Add a Chapter

* Open chapters/index.html and your chapter's name to the yaml list of chapters.
* cd into chapters/ and create the directory for the chapter name. Downcase the name and replace spaces with underscores.
* add an index.html file that uses `layout: default`. For convenience, just copy the index.html from another chapter and update the yaml frontmatter to reflect the name of your new chapter.

For example, to add a chapter called "Dates and Times", you would add it to the chapters array in `_config.yaml` file:

{% highlight yaml %}
chapters:
- Introduction
- Errors
- Testing
- Dates and Times
{% endhighlight %}

...and then create that chapter in the file system:

{% highlight bash %}
cd chapters
mkdir dates_and_times
{% endhighlight %}

Now create a new page in that chapter (remember to add its YAML front matter) and once jekyll regenerates the chapter index, your new page should appear.

# FAQ

## Can I Edit An Existing Recipe?

Yes. Please improve anything and everything! Be sure to test your changes and make sure that your solution really is better.

## I Have a Really Efficient Solution, But It's Not As Readable As the Existing Recipe. Should I Add It?

See the "Weird Recipe" note above. Do real people in the real world ever hit the performance constraint? If so, then by all means, add your strategy to the existing solution, and be sure to explain why your solution is not idiomatic. If a reader really has that problem, they'll be glad for the extra options.


## I Found a Typo. Is That Enough of a Fix? Does That Count?

Absolutely!
