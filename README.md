# DND Creatures

A DND 5e app that randomly chooses a DND creature at the click of a button. Uses the [https://www.dnd5eapi.co](https://www.dnd5eapi.co) API.
​
> As a Dungeon Master or a Druid, there are many creatures to choose from. But when time is running out, the possibilities seem endless.
​

You can try out the demo here: [Link](https://dnd-creatures.vercel.app)
​
## Technologies Used
* Sveltekit - For server side rendering, and minimal build sizes.
* Tailwind CSS - For its design system

## What I Learned
* Using async/await with the Fetch API
* Using the `on:` directive for event listening in Svelte
* How important adding the site's title and meta description is for SEO
* Randomizing the results before it is shown
* That there are 332 monsters in DND 5e and possibly even more

## What I Also Wanted To Do
To make it more useful, I would want the app to **show additional info of the creatures**. This would require another fetch to be made. While I've done those in the past (complex api repos), this would be my first time with the await operator so I wasn't sure if that would add extra complexity.

I also wanted to **add unit tests**. For an app like this, other than ensuring that the API data renders, the rest is straightforward. Being new to the Svelte ecosystem and not fully understanding how Jest works in Svelte, I opted to not dig deeper.
