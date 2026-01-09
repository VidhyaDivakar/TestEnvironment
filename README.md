## Test Environment

Here I will be testing my work alongside an webpage rendered by Jekyll theme. Testing and learning html, markdown and Jekyll.

notes for styles:
@import "ctastyle";  // imports _ctastyle.scss in [https://github.com/VidhyaDivakar/opentelemetry.io/blob/End-user-resources-Webpage-update/assets/scss/_styles_project.scss](https://github.com/VidhyaDivakar/opentelemetry.io/blob/End-user-resources-Webpage-update/assets/scss/_styles_project.scss)

### How to render this to the HTML site

In the Terminal, use `bundle exec jekyll serve` and open your browser at `http://localhost:4000`

#### How to get back to the prompt after bundle exec

Problem Statement:

[#008CBA`; color: white; ...&#34;&gt;Button Link](/your-link)

when i used this tag, the button is displayed in the Vscode .md file but it is not displayed in the github.md file. However, the button with proper link is displayed in the jekyll site. So why we need this additional css/scss? If this renders in Kekyll site, will it render in higo site too?

Answer:

**VSCode .md preview:** Shows the styled button because VSCode renders HTML/CSS in markdown preview

**GitHub .md file:** Doesn't show the button because GitHub  **strips inline styles for security reasons** . GitHub sanitizes HTML and removes `style` attributes.

**Jekyll site:** Shows the button because Jekyll processes the markdown and renders the inline HTML/CSS as-is into the final website.

**Hugo site:** Will also render the button! Hugo, like Jekyll, processes markdown and preserves inline HTML.

#### Why you need seperate CSS/SCSS?

* You want cleaner markdown files (no long style attributes)

* You want consistency (change button color once, applies everywhere)
* You want to maintain styling separately from content
* You want advanced features (hover effects, variables, responsive design)
* You're migrating from Jekyll to Hugo and want better organization

#### Linking the Custom.scss to `<head> tag.`

In this case, it is in the index.html file.

##### For Hugo site add

{{ $scss := resources.Get "scss/custom.scss" | resources.ToCSS }}
`<link rel="stylesheet" href="{{ $scss.RelPermalink }}">`

##### For Jekyll Site

Add '`<link rel ="stylesheet" href="{{'/assets/scss/custom.scss' | relative_url }}">`
