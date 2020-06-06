## Problem

The GitHub wiki web editor doesn't allow image upload. The modal window only support image URL. Which means, we may use 3rd party service like Imgur to host images.

But, what if we want to host the images on GitHub without relying on 3rd party services? This is my experiment to test if it's possible to upload images directly to wiki's repository.

## Status

Working & doable. See the steps below.

## Requirements

- If you're using GitHub free plan, you need to make a **public** repository
- If you're using GitHub paid plan, nothing to worry
- Next, go to your repository settings page and enable Wiki feature inside it

## Steps

1. Go to your wiki page ([example](https://github.com/zulhfreelancer/github-wiki-images/wiki))
2. Create a page (any title and body would work)
3. Open terminal and run the following commands:

    ```
    $ cd /path/to/your/projects/folder
    $ git clone git@github.com:your_github_username/your_repo_name.wiki.git # notice that ".wiki."
    $ cd your_repo_name.wiki
    $ mkdir images # any folder name would work
    $ # copy the image that you want to use in GitHub Wiki into this newly created 'images' folder
    $ git add .
    $ git commit -m "Add an image"
    $ git push origin master
    ```
    
4. To use the image, use this format inside the wiki pages: `[[/images/path/to/image.ext]]`. For example, let say your image name is `github-logo.png` inside `images` folder, it will be `[[/images/github-logo.png]]`.

5. That's all. You can use the Git workflow above to update the wiki pages locally too because they are just Markdown files. Just remember to always run `git pull` command before start editing any Markdown files.

## How It Works?

TL;DR - you have two repositories; application/code repository (main) and wiki repository.

The contents of your code that live in your `https://github.com/your_github_username/your_repo_name` are different from the contents that live inside the wiki section i.e. at `https://github.com/your_github_username/your_repo_name/wiki`.

The above steps only copy and amend the contents in the wiki section. Hence, you don't need to upload the images to your repository code area — unless the image is shared between your application and wiki pages.

Any modifications made (i.e. adding a new image) to the wiki repository won't add any new commits in the repository code area. Instead, it will be reflected under your GitHub wiki page's history ([example](https://github.com/zulhfreelancer/github-wiki-images/wiki/Home/_history)).

By using this approach, you will be able to keep your main repository commits history clean and you don't need to create any dummy issues or PRs just to upload files and grab their links for wiki usage.

Thoughts? Let's chat on [Twitter](https://twitter.com/zulhhandyplast)!
