# readmore

Client-side Javascript supporting "read more" and "read less" links which show and hide content on a web page.

The user sees a link which says "...read more" at the end of a section of text. 
When they click it, they see more content, and a link that says "read less".
And clicking "read less" hides the extra content again.


To use, mark some HTML element which contains all the relevant parts with the 
class "readmore-context".

Within the readmore-context element, incude tags like:
```
<a href="#" class="readmore">... read more</a>
<a href="#" class="readless"> read less</a>
```

You can change the text "...read more" and "read less" to be anything you want.

Then mark other elements inside the readmore-context element with the class "readmore".
These elements will be initially hidden. They will appear when the user clicks the "readmore"
link and be hidden again when the user clicks the "readlist" link.

You can mark many kinds of elements, including span, ul, ol, div, p, table, etc.
However, all elements except span will be revealed using display:block. So if an
element should be display:inline, wrap it in a span and put the "readmore" class on the span.

NOTE: Do not put your "readmore" link inside of an element which will be hidden.

Example:
```
<div class="readmore-context">

<p>This text is always displayed but<a href="#" class="readmore">... read more</a>
<span class="readmore"> this text is only displayed when the user clicks the reamore
link.</span></p>

<p class="readmore">And this paragraph is only displayed after the user clicks the
readmore link.</p>

<a href="#">readless</a>

</div>

```

index.html has links to some example pages, which you can play with online at
<a href="https://fpassow.github.io/readmore">https://fpassow.github.io/readmore</a>

Thanks!

