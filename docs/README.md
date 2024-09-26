# Instructions for files in UN-OG-Training/docs
The files in this directory `UN-OG-Training/docs/` include images and all the files necessary for rendering the Jupyter Book documentation.


## Logo optimized for GitHub and (X) Twitter

One image [`UN-OG-Training_logo_gitfig.png`](docs/UN-OG-Training_logo_gitfig.png) is only used for the GitHub social preview image. GitHub suggests that this image should be 1280x640px for best display. The image we created [`UN-OG-Training_logo_long.png`](docs/UN-OG-Training_logo_long.png) is natively 500x346px. We do the following to resize the image.

1. Open the image in Adobe Photoshop: **File** > **Open**
2. Open the **Image Size** dialogue:
3. Adjust the canvas size: **Image** > **Canvas Size**. Because the 500x346px image is taller than the optimal 1280x640px GitHub size, we first adjust the canvas size. We have to add some width. So here adjust the width to 692px [`346 * 2` or `346 * (1280 / 640)`] and keep the height at 346px.
4. Adjust the image size: **Image** > **Image Size**. Now adjust the image size to the GitHub optimal 1280x640px. The dimensions will be correct and nothing will be stretched.
5. Save the image as [`UN-OG-Training_logo_gitfig.png`](docs/UN-OG-Training_logo_gitfig.png).
6. Upload the image [`UN-OG-Training_logo_gitfig.png`](docs/UN-OG-Training_logo_gitfig.png) as the GitHub social preview image by clicking on the [**Settings**](https://github.com/EAPD-DRB/UN-OG-Training/settings) button in the upper-right of the main page of the repository and uploading the formatted image [`UN-OG-Training_logo_gitfig.png`](docs/UN-OG-Training_logo_gitfig.png) in the **Social preview** section.


## URL for iframes versus text

* For the iframes that show PDF files stored on Google Drive, the URL needs to be adjusted to say "preview" instead of "view". For example an iframe HTML code block referencing the following BYU ACME Lab might look like the following, where the URL in the `src` field is just copied from Google Drive. Note it has the "view" specification.
```html
<div>
  <iframe id="inlineFrameExample"
      title="Inline Frame Example"
      width="100%"
      height="700"
      src="https://drive.google.com/file/d/1gAam1i1Gy0YgULT92ul72DUqRCb4q2fA/view?usp=sharing">
  </iframe>
</div>
```
This code will produce a "Google Drive Forbidden Error 403" in the rendered Jupyter book. The solution is to change the URL from "view" to "preview". The following example is how we correctly specify these iframes in this Jupyter book.
```html
<div>
  <iframe id="inlineFrameExample"
      title="Inline Frame Example"
      width="100%"
      height="700"
      src="https://drive.google.com/file/d/1gAam1i1Gy0YgULT92ul72DUqRCb4q2fA/preview?usp=sharing">
  </iframe>
</div>
```
For all other references to PDF files stored on Google Drive, we use the standard "view" format of the URL.


## Need for text after footnotes sections

Jupyter Book gives an error for markdown code that has footnotes immediately after a section heading specified as follows.
```markdown
(SecName)=
## Footnotes

[^footnote_name]: Generic footnote text.
```
The error we would get in the Jupyter book text looked like the following.
```
/Users/richardevans/Docs/Economics/OSE/UN-OG-Training/docs/book/python/NumPy.md:127: ERROR: Document or section may not begin with a transition.
```

The Jupyter book would compile fine. But we didn't love the error messages. The following addition of some text between the "Footnotes" section title and footnotes solved the problem.
```markdown
(SecName)=
## Footnotes

The footnotes from this chapter.

[^footnote_name]: Generic footnote text.
```
