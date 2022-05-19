# Vue/Front-end Coding Challenge (cue dramatic music)

### Overview

Your challenge is to integrate with an API to pull data and display it as shown in the mock below. We have an internal API for [Cats](https://vue-mock-api.openlypreview.com/api/cats) and another for [Dogs](https://vue-mock-api.openlypreview.com/api/dogs). Use whichever you prefer! (both follow the exact same data structure)

Your users should be able to:
- See all results from the API on the homepage (we've limited each response to 10 items)
- Filter by breed and by category
- Click the more info buttons to see more detailed information in a modal
- Click the hearts to save their favorites
- Click the favorites link in the header to view all their favorites on a separate page

![image](/mock.jpg)

### Objectives

1. Your layout should be responsive, and your application should be fully usable on desktop and mobile.
1. The favorites count in the header should increase and decrease as the favorite hearts on the cards are toggled.
1. The favorites link in the header should link to a separate page.
1. [Bonus] Feel free to get fancy with animations if you have the time.
1. [Bonus] You can optionally add search functionality.

### Considerations

- Please don't spend more than 4 hours on this. We're by no means setting a hard deadline, we just want to be considerate of your time.
- Don't worry if you can't complete all the objectives in the time allotted. It's less important to us that everything functions 100% perfectly and more important for us to see how you thought through problems, what questions you asked, and how you handled vague requirements.
- We'd like this to be interactive. Please push your code up to this GitHub repo regularly to allow us to see your progress. Let us know in the Slack channel when you're ready for someone to take a look at the progress and give you code-review feedback. The best interview code challenges are ones where we collaborate.
- Ideally, we'd like to have this completed within a week but we're usually very accommodating if that needs to be extended—just let us know.

## Getting Started

We use [Nuxt](https://nuxtjs.org/) and [Tailwind CSS](https://tailwindcss.com/docs) for all our frontend repos. We set up this project the same way so you can hit the ground running.

## Build Setup

```bash
# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```

**Good luck!**
