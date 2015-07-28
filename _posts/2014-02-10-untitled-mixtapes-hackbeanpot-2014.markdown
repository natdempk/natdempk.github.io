---
title:  "Untitled Mixtapes - HackBeanpot 2014"
date:   2014-02-10 12:00:00
<!--description: Thriller Comedy Horror-->
---

This weekend I participated in a 48 hour hackathon for Boston-area college students called [HackBeanpot](http://hackbeanpot.com/) with [Sanders Lauture](https://twitter.com/golf1052) and [Zack Hickman](https://twitter.com/ZackHickman). It was put on by some awesome people from Northeastern University who also do cool stuff like run [NU ACM](http://acm.ccs.neu.edu/) and [NU Hacks](http://hacks.io/). They like to make stuff and create events for people who like to make stuff, which is super cool. Mad props to them. It was a ton of fun, and was run extremely well. If you’re a college student near Boston who makes stuff or wants to make stuff, you should definitely come next year.

## Our Hack

We created a mixtape generator called Untitled Mixtapes that creates a 6-14 track mixtape based on a user-provided artist and song. You might be thinking that sounds a lot like Pandora, Spotify Radio, Songza, or one of another million online radio services. We tried to stray away from those, by aiming to create a cohesive musical experience of similar enjoyable songs with a strong beginning and end. We saw a mixtape as a contained musical story and tried to translate some of the human selection factors into quantifiable metrics that an algorithm could use. I think we succeeded in creating listenable mixtapes. There were a few different options and ideas we wanted to add that we didn’t get to, but the mixtapes generated were up to our standards.

## Technical Factors

For the frontend, we used Bootstrap and a little jQuery to make our site look pretty and power some of the UI elements like the sliders. We also used the Spotify Play Button to create a web playlist to present to the end user. We wrote the backend in Python, utilizing Flask, pyechonest, and pylast. To create the mixtapes, our first step is to get a bunch of recommended artists from last.fm. We used them because I liked their recommendations from using their site in the past. We then take those recommendations, and get songs for those artists from EchoNest, along with a ton of other information about the tracks. If the user wants more diversity, we repeat this more to branch out further from the original artist. From those tracks we pick a bunch with similar energies, arrange them by a couple more attributes like length and BPM, and put the best ones into a playlist keeping the artists mostly unique. We make sure to start and end with the same artist that the user chose, as that’s usually their favorite. Additionally, we try to start with the song they picked, as they probably want to hear that in the mix, and we’re kinda assuming that they picked a song they want to hear to kick things off.

From there we use EchoNest again to get a list of Spotify track IDs. We had a bunch of problems trying to use the Spotify API at first, which ate up a lot of time. Our original plan was to have the user authorize with Spotify, and then create our mixtapes as playlists on their Spotify account, but we couldn’t get pyspotify to create playlists and add songs within a reasonable time. We gave up on that after fiddling with it for a long time. (Too long!) We realized afterwards, that we could use the Spotify Play Button to create a widget from a list of song IDs, so we ended up using that to good effect. With this, the end user just clicks play in browser, and it either takes them to the Spotify Web Player, or starts playing the in the Spotify Desktop Client, which is pretty much perfect. They can even save the list of songs as a playlist from there, so from a UX standpoint we didn’t have to sacrifice much. The biggest loss there was time, meaning we didn’t get to improve our hack as much as we would have liked to.

## Human Factors

I think we did a pretty good job of planning and fleshing out our idea at the beginning, but that we could have spent a little more time looking into APIs and methods of doing things. We structured our EchoNest API calls poorly, which made generating mixtapes slower, so we implemented threading to deal with that somewhat, but in the end it would have been better and faster to just structure them well in the first place. We also had a ton of Spotify issues, which we probably could have avoided if we had just looked into another way of showing off our results earlier. That would have saved a lot of time to use elsewhere. Next hackathon, I would try to delve deeper into the docs and options for everything we are using before coding anything, as it seems like that would always save time in the end.

Over the course of the hackathon, I think we did pretty well in maintaining energy levels, despite endless coding and a general lack of sleep. I came to the event after being at work all day on Friday, so I was pretty spent from the beginning, but tons of caffeinated drinks along with strategic naps kept me alive and semi-alert. I think the best thing we did, was take a few-hour break Saturday evening, to go home for a bit to sleep and shower. That meant we were refreshed and ready to code and debug for the final 12 hours. In total, I think I slept for around six of the forty-eight hours, which was just enough. Any less and I wouldn’t have made it to the end. I don’t know how people who stayed up the whole time did it.

## Results

Untitled Mixtapes won Best Use of APIs, which was sponsored by SmarterTravel! It was pretty sweet to win. We got an awesome plaque to show off!

## Future Plans

We are currently working on rewriting/refactoring a couple parts of our site to be more efficient. Once we do that, we are going to release it to the world. We’ll also put the source up on Github. I’ll tweet about that when it happens, so follow [@natdempk](https://twitter.com/natdempk) if you’re interested.

## Thanks

Thanks to all the organizers of HackBeanpot for putting on an awesome hackathon. They went above and beyond in providing us with food and resources so we could focus on hacking. This was my first hackathon and they made it great!

Thanks to all the sponsors for making the event possible. Tripadvisor, HubSpot, Intuit, SmarterTravel, PayPal, and Wayfair were all great about providing swag, engineers, enthusiasm, advice, judges, and prizes. Thanks to the Cambridge Coworking Center for the space, it wouldn’t have been the same without the great work environment. I look forward to more in the future!
