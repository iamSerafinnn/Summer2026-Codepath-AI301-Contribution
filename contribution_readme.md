# Contribution [2]: Refactor Home Website Blog Layout UI

**Contribution Number:** 2 
**Student:** Serafin O. Gargantiel III.
**Issue:** https://github.com/apache/hertzbeat/issues/2075
**Status:** Closed and not merged. The issue #2075 was resolved through another PR #4219

---

## Why I Chose This Issue
I chose this issue mainly because it is related to frontend web development which I have worked on before with notable skills using React, HTML, and CSS. The Hertzbeat website is built using Docusaurus, which upon researching on it, it is a React-based static site generator by Meta. This blog UI would contain writing with real React components which I have worked on before and I feel confident in doing.

In the hopes of doing contributing to this issue, I hope to learn how to make websites more polished and looking more professional for its users. In top of that, I get to learn a new React-based open source static site generator, Docusaurus. It is a new skill I hope to learn in this project and will continue to carry it forward to the future for future Web and Application development work!
---

## Understanding the Issue

### Problem Description
That their current blog layout of the HertzBeat website is outdated and lacks modern design. The owners of the website asked to refactor their UI blog website to look more professional, contemporary, and appealing to users, with a reference to a Answer Blog with a design that they would like their blog website to be similar to.

### Expected Behavior
This new blog page of HertzBeat should display posts using a modern card-based grid layout similar to the Answer Blog site they referenced. It will contain better typography, better use of whitespace, and a better polished appearance overall.


### Current Behavior
The owners current HertzBeat blog site uses a default Docusaurus blog layout. It has minimal customization and a simple plain list styling design that feels outdated compared to modern documentation and community sites.


### Affected Components
In the HertzBeat blog site repository, all Docusaurus based code are stored in their "home/" directory. Here you will find the blog layout components that we will use to refactor the layout and uses Docusaurus swizzling to override the default blog UI.

---

## Reproduction Process

### Environment Setup
I cloned the fork locally in my computer terminal. In the files, it contains a "home/" folder containing the UI components. I navigated to this directory and ran npm install, than npm run start to start the local blog site. However, because of multiple issues of not being able to run and launch the site, I had to switch to Node version using nvm as this projects requires Node >= 20 installed. I use v20.20.2 via nvm and manage to get the local site server to launch properly at a http://localhost:3000/blog

### Steps to Reproduce
1. Cloned the HertzBeat site blog UI and navigated to the "home/" directory.
2. To be able to launch the site server, install Node v20 with nvm, and then run "npm install" and "npm run start"
3. You will get a local browser of of "http://localhost:3000/blog" in your browser.
4. In a new tab, open this local reference site of "https://answer.apache.org/blog/" to get an idea of what the final UI 
   layout would look like.
5. Now, compare the two sites. You will see that our local site displays a plain generic vertical lists with no card containers, images, or even grid structures. The reference site on other hand displays those, show a modern design.


### Reproduction Evidence
- **Commit showing reproduction:** https://github.com/iamSerafinnn/Hertzbeat-Site-Refactor/tree/refactor-blog-ui
- **Screenshots/logs:** [If applicable]
- **My findings:**
The the blog site server is using Docusaurus's default out of box blog layout with no custom components. A "home/src" directory is what stores custom React components and swizzling Docusaurus will be needed to override the default blog list componnts to apply changes.
---

## Solution Approach

### Analysis
The root problem is that the HertzBeat local website has not been customized and will default maintain the Docusaurus blog layout. Docusaurus ships with basic list-style design out of the box and without any swizzling to the components, it will stay that way.

### Proposed Solution
We will use the Docusaurus component, swizzling, that helps ejects and overrides components in the default blog list. After overriding, we will then rebuild the whole HertzBeat local site into a modern card-based grid layout with the use of React and CSS, similar to the reference design site, answer.apache.org/blog.

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** The HertzBeat local blog page uses the default Docusaurus blog layout that renders posts as a plain vertical list. What we want is to refactor that into a modern card-based grid layout design.

**Match:** Our answer apache website, answer.apache.org/blog, uses a similar Docusaurus setup with some customized blog components in its design. The "home/src/" directory in HertzBeat is where custom components already exist and where new ones will be added.

**Plan:**
1. Explore - Explore the "home/src/" directory in HertzBeat to understand the component structures.
2. Swizzle - Use Docusaurus swizzling to eject and change default Docusaurus components.
3. Build   - Build a custom card-based grid layout with React, JSX, and CSS.
4. Style   - Style the cards to match the design on the reference answer site.
             (Include images, tags, info, and whitespace)
5. Test    - Test the new refactored layout at a local server of http://localhost:3000/blog.
6. Commit  - Commit the changes to the "refactor-blog-ui" branch that I created and open a pull
             request to apache/HertzBeat.

**Implement:** https://github.com/iamSerafinnn/Hertzbeat-Site-Refactor/tree/refactor-blog-ui

**Review:** Follow the HertzBeat contributing guide commit format: "[docs]feature: refactor blog layout ui"

**Evaluate:** Verify the updated blog page at localhost:3000/blog visually matches the card-based layout of answer.apache.org/blog before submitting the pull request.


---

## Testing Strategy

### Unit Tests / Integration Tests

- [✅] Automated Tests:
I have not added any unit or integration tests for my contribution. My changes
only affect the UI of HertzBeat's Docusaurus documentation site in the "home/"
folder, which is not covered by the project's unit or e2e test suites. There
are also no existing test files or helpers for the site's React components
that new tests could follow. 

### Manual Testing
Ran "npm run start" locally with Node v20.20.2 and verified the blog page at
http://localhost:3000/blog. It renders a 3 column card grid with tags, titles,
descriptions, dates, and author names that has a responsive behavior at
smaller breakpoints and hover effects on cards. I compared the result
side-by-side against the reference design at https://answer.apache.org/blog/.

---

## Implementation Notes

### Week 1 Progress
Used a docusaurus swizzling to eject the default BlogPostItems component and created a custom
card-based grid layout for a starting refactored layout.

### Code Changes

- **Files modified:**
    - "home/src/theme/BlogPostItems/index.js" - (Created) Swizzle to refactored card grid layout
    - "home/src/theme/BlogPostItems/styles.css" (Created) Styles the BlogCards and the Grids
    - "home/src/pages/index.js" - (Modified) Fixed broken hero logo image path (was pointing at a
       raw filesystem path instead of a static asset URL) and added a ".heroLogo" class to size it
    - "home/src/pages/styles.module.css" - (Modified) Added ".heroLogo" sizing rule
- **Key commits:** 
    - https://github.com/iamSerafinnn/Hertzbeat-Site-Refactor/tree/refactor-blog-ui
- **Approach decisions:**
    - Used swizzling instead of wrapping. This allows me to have full control of over the blog list
      rendering into a card grid instead.
    - Used CSS Grid for layout to keep dependencies minimal instead of using a UI library.

---

## Pull Request

**PR Link:** https://github.com/apache/hertzbeat/pull/4182

**PR Description:** 
Closes #2075

Before the process of refactoring, the layout of the website were just a plain list of written text documentation. There is no structured layout of cards, images, and modern styling.

I refactored your HertzBeat site's UI for its home website blog to a more modern layout of card-based grids for the issue #2075. It is written in Docusaurus and React JS open source frameworks for frontend and web development.

After refactoring the first thing the user sees is a main title page of HertzBeat, a big title, slogan, and a quickstart button that brings the user to the list of documentation like the previous design. The user can further scroll down and find blog cards of three core features and a swiper of images below it. This creates a clean first impression of a modern like design with images and components to the site.

By using a refactoring feature provided by Docusaurus, component swizzling allows me to replace and wrap default list-style theme components made by the maintainers themselves and transformed them into my own custom React Code in index.js and style.css.

Upon continued progress, a separate fix made by a different PR, #4219 was eventually merged by the maintainers and not this. The issue #2075 was closed and the issue was resolved by a different PR.

Checklist
 [✅] Contribution Guide: I have read the Contributing Guide
 [✅] Documentation & Comments: I have written the necessary document or 
      comment.
[N/A] Unit Tests: No necessary unit tests cases is  
      necessary for this fix as it just depends on UI redesign and not logic or bug related problems.
[N/A] API: No API is update or added in this program. 
      This is just a means of redesigning a website interface using React components.


**Maintainer Feedback:**
- July 4, 2026: Maintainer @Duansg merged the latest "master" into my "refactor-blog-ui" branch to keep the PR up to date and mergeable. No review changes requested yet.
- Response: Synced my local branch with "git pull" to stay current. Monitoring the PR for review comments.

- July 12, 2026: Applied fixes from GitHub Copilot's automated review Also fixed the HertzBeat logo not rendering in the hero title, don't know how that happened.
- Response: Committed and pushed all changes to the PR branch. I am still awaiting maintainer review.

- July 26, 2026: The maintainer, @tomsun28, closed my PR #4182. @tomsun28 mentioned that the issue #2075 was resolved by another contributor PR #4219. It had a much broader scope of categories that are backed by "blog/tags.yml", cover images, and localized label/dates. This PR was merged instead of mine.
- Response: I acknowledged the closure and respected the maintainer's decision. No further action taken from me.


**Status:** Closed and not merged. The issue #2075 was resolved through another PR #4219

---

## Learnings & Reflections

### Technical Skills Gained

- First hand experience on docusaurus swizzling to override its 
  default theme components.
- Learned how to build a custom React card grid from useBlogPost
  () hook.
- First time working as an open source contributor in GitHub.

### Challenges Overcome

- Learning docusaurus component structure despite having no   
  experience working with the framework.
- Issues trying to troubleshoot the right Node version for the 
  project. Apparently, Docusaurus swizzling is uncompatable with the version of Node.js I had installed by default. Compatability was a factor here as the it required Node v20+ and setting up the nvm.

### What I'd Do Differently Next Time

- I constantly have to switch to node versions to run this program. I worked on other projects using Node.js and apparently, working with Docusaurus Swizzling requires me to use a newer version of Node.js. For next time, I can try to set up a global default Node.js version using NVM (Node Version Manager). Using this nvm default version would prevent me from having to manually switch node versions per session.

- Refactoring was only made with a main page redesign. For further improvements, I can always other parts of the blog site like the text documentation itself. Create more structured layout of texts and even convert them into more unique card designs.

- I have never explicitly @mentioned or requested review from the maintainer after redesigning it myself and open the PR. Upon refactoring, I just open a pull request and just waited for the maintainer to find it. For next time contributions, I can always reach out to the maintainer after finishing my work so that they can review it more quickly.
---

## Resources Used
- [Apache HertzBeat Issue #2075](https://github.com/apache/hertzbeat/issues/2075)
- [Apache Answer Blog (design reference)](https://answer.apache.org/blog/)
- [Docusaurus Documentation](https://docusaurus.io/docs)
- [HertzBeat Contributing Guide](https://github.com/apache/hertzbeat/blob/master/CONTRIBUTING.md)
