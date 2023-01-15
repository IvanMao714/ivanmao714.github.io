---
title: Gatsby blog deploy to github
date: 2023-01-13
tags:
  - Gatsby
  - Blog
  - Github
---

Documents (ENG)

- [Install](#install)
- [Basic Settings](#basic-settings)
- [Writing posts](#writing-posts)
  - [Markdown YAML Front matter](#markdown-yaml-front-matter)
- [Deploy](#deploy)

<br/>

## "Borderless", Gatsby Blog Starter(Theme)

Static websites created with Gatsby,  
Borderless Blog Theme.

This document is based on the distribution to Github Pages.

**Borderless DEMO WebSite**

- Simple design with minimal color without border
- Create Markdown Posts (Markdown + emoji, ktex)
- Search Engine Optimization (SEO)
- Support Reader Mode in posts such as Safari browser
- Google Analytics support
- Google Adsense support
- Disqus comment function

<br/>

## Install

There are two ways to get started with this blog.

1. Use after the Repository Fork
1. Use after the Repository Clone

### ! Important

**Don't work on master branch.**

If you go through the steps above, the branch you're working on is develop.  
Start working on this develop branch. You can modify the develop branch or create a branch separately from the develop branch.

The master branch is used for deployment, and the built file is located.  
You can work on the develop branch and deploy it using the deploy command.  
The deploy command automatically deploys to the master branch, which does not have direct access.

### 1. Use after the Repository **Fork**

- After Fork the Repository,

1. `Setting > Option - Repository name`  
   Rename the Repository to "**username**.github.io"
1. `Setting > Branches - Default branch`  
   Change the default branch. Select **develop** and press the Update button to proceed.
1. clone your Repository.
1. `$ npm i` install packages
1. `$ npm start` Start local development environment
   Check URL "localhost:8000"

### 2. Use after the Repository **Clone**

```shell
$ git clone -b develop --single-branch https://github.com/junhobaik/junhobaik.github.io.git [SITE_DIRECTORY]
$ npm install
```

This procedure clones the repository based on the develop branch.  
Then install the required packages.

```shell
$ npm start
```
Start local development environment  
Check URL "localhost:8000"

<br/>

## Basic Settings

Modify the default settings for you.

### Modify `./_config.js`

`_config.js` example

```javascript
module.exports = {
  /** Site MetaData (Required all)*/
  title: `Dev.White`,
  description: `Junho Baik's Development Blog`,
  author: `Junho Baik`,
  language: `en`,
  siteUrl: 'https://junhobaik.github.io',

  /** Header */
  profileImageFileName: 'profile.png',

  /** Home > Bio information*/
  comment: 'Jr. Web Front-end Developer. / javascript, react ...',
  name: 'Junho Baik',
  company: '',
  location: 'Korea',
  email: 'junhobaik@gmail.com',
  website: 'https://junhobaik.github.io',
  linkedin: '',
  facebook: '',
  instagram: 'https://www.instagram.com/junhobaik',
  github: 'https://github.com/junhobaik',

  /** Post */
  enablePostOfContents: true,
  disqusShortname: 'junhobaik',
  enableSocialShare: true,

  /** Optional */
  googleAnalytics: 'UA-123123123-0',
  googleAdsenseClient: 'ca-pub-5001380215831339',
  googleAdsenseSlot: '5214956675',
};
```

| 설정                                             | 타입                         | 설명                                                         |
| ------------------------------------------------ | ---------------------------- | ------------------------------------------------------------ |
| title                                            | (required) String                | Title of the site. Title text in the header. Enter the title of each webpage. |
| description                                      | (required) String                | Description of the site                                                |
| author                                           | (required) String                | Author of the site                                               |
| language                                         | (required) String                | Site default language. 'en' for English, 'en-US' is also possible by adding country code. |
| siteUrl                                          | (required) String                | Enter the address of your website. If the address is not present at deployment time, many errors can occur. |
| profileImageFileName                             | String                       | Locate your profile picture in the path `./src/images` and enter the filename of the image. It enters the image next to the title of the header. If there is no input, it shows a random image. |
| comment, name, company, location, email, website | String                       | This is the personal information shown on the left side of the Home (index) page. If not entered, the item is not output and all values are entered as strings. |
| linkedin, facebook, instagram, github            | String                       | These are the social icon links that will appear under Personal Information on the left side of the Home (index) page. Clicking on the icon will take you to that link. Please enter full link, not ID |
| enablePostOfContents                             | (required) Boolean (true, false) | Set whether the table of contents appears in the post.                 |
| disqusShortname                                  | String                       | You can activate the comment function. After creating a site in disqus, enter the shortname of the site here. Emptying the value disables the comment feature. |
| enableSocialShare                                | (required) Boolean (true, false) | Set whether to display post social sharing icons at the bottom of the post. |
| googleAnalytics                                  | String                       | You can activate Google Analytics. Enter your TrackingID. |
| googleSearchConsole                                  | String                       | content value in HTML tag of google search console ownership verification, ex.'w-K42k14_I4ApiQKuVPbCRVV-GxlrqWxYoqO04KDbKo' |
| googleAdsenseClient                              | String                       | Client input of Google AdSense when activating GoogleAdsense. In addition, change the number corresponding to Client in `./static/ads.txt` to the number of your client.        |
| googleAdsenseSlot                                | String                       | Enter Google AdSense Slot when activating GoogleAdsense.          |

String (String) values are not required to be empty ''

Disqus Comments, Google Analytics, and Google Adsense features are disabled during local development. After deployment, you can use these features.

<br/>

## Writing posts

Posts are written in Markdown.

- Markdown
- emoji support
- ktex support

Your post will be located in the `./_posts` folder.  
Your draft post will be located in the `./_drafts` folder. (Draft posts are visible during local development, but not on the distributed web)  
The `_posts` folder and the` _drafts` folder must exist. ** Do not delete both folders **

The title of the file becomes the address of the post post.
If a date is entered, such as in Jekyll's post file title format, the date is excluded from the address.

ex 1. `./_posts/first-post.md`  
address: https://junhobaik.github.io/first-post

 2. `./_posts/2019-12-31-first-post.md`  
address: https://junhobaik.github.io/first-post

**Create post with image**

When embedding an image inside the markdown, the structure is as follows

Example of creating a post that will have an address of `/first-post`
After creating `./_posts/first-post` folder,   
Markdown files have the title `index.md`,  
Place image files in that folder.

```
  _posts/
    first-post/
      index.md
      image-file-1.png
      image-file-2.jpg
      ...

```

### Series Posts

When you write several posts on one subject as below, you can use the series function to indicate that the post is included in the series.
With the series feature, you'll see a list of series posts at the top of the post.

-Create a blog, install
-Create a blog, setting up
-Create a blog, Distribution

If you write a post like this, write the file name as below.

- `development-blog_1.md`
- `development-blog_2.md`
- `development-blog_3.md`

The number after the underbar(\_) is the number of the series.  
The file name before the underbar(\_) must be the same.  
There must be only one underbar(\_) in the file name.  
Do not mix numbers and letters after the underbar(\_).

### Markdown YAML Front matter

At the top of a Markdown post, enter the information for that post.
Enter the information in two `---` s as shown below.

```
---
title: title here...
date: 2018-01-01
tags:
  - javascript
  - ES6
keywords:
  - keyword1
  - keyword2
---

contents here...
```

| Variable   | Description                                                                     |
| ---------- | ------------------------------------------------------------------------------- |
| `title`    | **(required)** Enter the title of the post. If special characters are included, enclose them in `" "`.    |
| `date`     | **(required)** Enter the creation date of this post                                        |
| `tags`     | **(optional)** Enter tag for post                                          |
| `keywords` | **(optional)** SEO meta keywords |

\+ All values are not enclosed in `''`, `""`.

#### data Examples

```
# date Examples

## Case 1
date: 2018-09-01

## Case 2
date: 2018-09-01 22:00:00

## 'Time zone' Not Support
## There is no error but ignores the time zone
date: 2018-09-01 20:00:00 +0900
```

#### tags & keywords Examples

```
# tags & keywords Examples

## Case 1
tags: onlyOneTag

## Case 2
tags: [tag1, tag2]

## Case 3
tags:
  - tag1
  - tag2
```

<br/>

## Deploy

Checklist before deploying

1. Make sure your Github repository is named username.github.io.
1. Make sure you have written siteUrl correctly in `./_config.js`.
1. Make sure the branch you are working with is not the master branch. (Please refer to the Install section for the relevant instructions)

```
$ npm run deploy
```

The deployment starts with the above command.
The commit is automatically made to the master branch.
It takes several tens of seconds, sometimes up to a few minutes, to be reflected.

You can now enter and verify your address.
