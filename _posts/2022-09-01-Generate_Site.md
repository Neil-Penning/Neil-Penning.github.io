---
layout: post
title:  "Generate Old Files"
date:   2022-09-01
permalink: /:categories/:year/:title:output_ext
categories: Task Github_Pages
---
# Problem
To start my Github Pages, I made a list of everything I've done off the top of my head [here](https://github.com/Neil-Penning/Neil-Penning.github.io/blob/bb522202272ef74ad62cf3f748d4162497e6f34c/index.markdown).
The list looked something like this:
```markdown
# Tasks
- 0000-00-00 Writing on PDFs on my iPad
- 0000-00-00 Bitwarden send-password

# Projects:
- 2020-04-__  [createsections](./Projects/createsections.md)
- 2020-06-00  [Arrow](./Projects/Arrow.md)
- 2020-10-00  [Twin Primes](./Projects/Twin_Primes.md)
- 2021-11-00  [The Working Plex Server](./Projects/Plex_Server.md)
- 2022-06-__  [Pixelfed]
- 2022-08-30  [Github Blog](./Projects/Github_Blog.md)
# Skills
- 2022-08-00  [My Class Workflow](./Skills/My_Class_Workflow.md)

# Explainations:
- 2020-11-00  [Animating the Heat Equation](./Explainations/Heat_Animation.md)
- 2021-04-00  [The Matthiu Group of order 7920 exists](./Explainations/7920.md)
- 2022-02-00  [K_7 is Planar](./Explainations/K7.md)
- 2022-04-00  [The Dehn Nielson Baer Theorem](./Explainations/DNB.md)
```
First, I got each entry in into a form parseable by bash:
```bash
$task $date $title $file_title
```

Then I wrote the following bash function
```bash
generate_site () {
    # $1 Category
    # $2 Date
    # $3 Title
    # $4 File Title
    file_path="./$2-$4.md"
    echo $file_path
    cp "$1.md" "$file_path"
    sed -i "s/0000-00-00/$2/g" "$file_path"
    sed -i "s/TITLE/$3/g" "$file_path"
}
```
to generate each blog post from a template file, and automatically set the date and title.

You can see the templates and the final script in [this github gist](https://gist.github.com/Neil-Penning/52817c10f7dc58f8c48c6667b907fbdb).


I put the generated files in Jekyll's `/_draft/` folder, which is documented [here](https://jekyllrb.com/docs/posts/#drafts).
The resulting change occurs in [this commit](https://github.com/Neil-Penning/Neil-Penning.github.io/commit/6e36033a19b8413974d414e5092c62083f8043ea).
