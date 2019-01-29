# College Football Recruiting App (~~Code Samples~~ & Screenshots)
This is ~~code samples~~ *(not yet...)* and screenshots from a private college football recruiting demo I worked on. 

The logo and name has been altered for anonymity. To my knowledge, this app never launched.

- [Work Summary](https://github.com/BretRoyster/college-football-recruiting-sample/blob/master/README.md#work-summary)
- [My React / React Native Experience on this Project](https://github.com/BretRoyster/college-football-recruiting-sample/blob/master/README.md#my-react--react-native-experience-on-this-project-brain-dump)
- [Screenshots](https://github.com/BretRoyster/college-football-recruiting-sample/blob/master/README.md#screenshots)

This is my most recent experience with React; a cross-platform mobile app (iOS and Android) and web app using React Native framework and ReactXP library respectively, which are both built on ReactJS framework. We also used React Redux, Redux Saga, and React Native Maps libraries for our app. Initially we started the app with the Expo.io tool set, but ultimately opted to eject the app to a 'pure' React Native project.


## Work Summary

*Mobile Development: android studio, apple xcode, google maps api, redux, redux-saga, react-native*

Startup client needed MVP of iOS and Android mobile apps for next round of investor fund-raising efforts.

I lead a team of 2 full-time front-end developers, 1-2 part-time front-end developers throughout the project, and myself as a senior full-stack developer.

- I was responsible for developing (1) the advanced front-end mapping features and (2) the entire Java / Spring Boot back-end server, as well as other features, bug fixes, improvements, etc.

- Also finished and refined majority of front-end development started by other teammates, which was necessary to shorten our integration/QA cycle to help meet client's cost constraints.

- Solely responsible for production-ready testing, debugging and fixing features prior to build releases. 

- Created and maintained scripts for build and dev environments. 

- Solely responsible for weekly builds in xCode and Android Studio, and deploys to iTunesConnect (Apple App Store and Test Flight) and Play Store respectively.

Client was very happy with overall outcome, and received an overwhelmingly positive response from their current investors.

**NOTE:** Client company logo and name have been replaced in screen shots to maintain privacy. 

## My React / React Native Experience on this Project (brain dump)

We had a new client that needed a college recruiting app created in iOS, Android, and web in roughly that priority.

After some discussion, it seemed like it was time to break into React Native.

### Front-end and Back-end Architecture

From an architecture standpoint, I built the backend for our RN project with using a [JHipster stack](https://www.jhipster.tech/) which is Spring Boot (Java), AngularJS as an admin interface (I opted not to use a React front-end simply because we were new to React and I wanted to keep that learning complexity directed at the user app and not the admin interface).

After establishing the back-end, my co-worker had settled on the majority of the architecture for the React Native app, which consisted of a fairly large (but complete) boilerplate pattern for "screens" and "components" (or smart and dumb components - our 'screens' held state and our (dumb) 'components' did not).

When I jumped into the React development I used https://reactnativeexpress.com to spin up, which was super helpful - I highly recommend it. And spent a couple hours with my co-worker on the phone to get an understanding of his Redux/Redux Saga 'boilerplate' pattern.

### State Management (Redux)

The state management was 'mostly' [React Redux](https://github.com/reduxjs/react-redux). For forms I opted to use the standard React state logic (and I instructed our team to do the same) - because I personally didn't see the benefit in all of the boilerplate overhead of Redux pattern for the form inputs. It just felt completely overkill and unnecessary. I also felt like it created a nice separation of intent - standard React state was used in very temporarily circumstances and React Redux was indented for everything else.

I looked into how easy it was to add [Redux Persist](https://github.com/rt2zz/redux-persist) to our architecture, but by the time I discovered it I didn't have time to confidently test it in that app and ensure it didn't have some kind of adverse effect that would create more cost for our customer - and it wasn't immediately needed either, even though it was really interesting to me.

This is a good time to mention, that this project was a client project and our client was very concerned with speed/cost and we didn't really have time to do things that didn't have an immediate and direct benefit that the client was specifically asking for - most of my projects in my previous roles were like that - even though sometimes I did find time to 'experiment' if I knew the risk was worth it. 

Redux Persist, could have been marginally worth it (it was supposed to be very simple to add) - I was just running into too many unknowns in React Native in general, so at that point I was operating us at the lowest risk I could. Additionally we were already using the local device storage to cache user credentials via a very simple pattern, and could easily use that for anything else we wanted persisted locally between user sessions - which there was one more minor thing we persisted, I believe, but I can't even recall what it was.

Anyway...

We also used [Redux-Saga](https://github.com/redux-saga/redux-saga) for our HTTP connections to the back-end Spring Boot (Java) server I developed. Honestly, after being exposed to alternative HTTP client approaches in React - Redux-Saga could feel possibly boilerplate 'heavy' again, but I would still use it in the future because I think it helps enforce a good clear pattern working with HTTP and React Redux.

### Gotchas! (ie. 3rd Party Integration Woes!)

One of the bigger, gotchas that happened on this project was discovering that (for some reason) [react-navigation](https://github.com/react-navigation/react-navigation) created terrible memory performance issues in Android for apps with larger sets of scenes/pages. So I was also exposed to [React Native Navigation by Wix](https://github.com/wix/react-native-navigation) which I thought was fairly straightforward to work with (despite some of their documentation being lacking).

Another challenge of that project was library integration like [React Native Maps](https://github.com/react-native-community/react-native-maps) and working with [Expo](https://Expo.io) (ie. trying to circumvent their constraints while still wanting to leverage their tools - eventually opting to just leave Expo completely because it was it was too much work to attempt to circumvent some of their architecture - and it was also a decision made mostly above my head - I would have liked to see how fast we could have iterated coding cycles back to the client using Expo, personally.)

Also leveraged open-source components like [NativeBase](https://nativebase.io/), and one other component library that I can't recall right now. We used them for a card swiper and tabs at least, possibly some other components.

### My Direct Contributions

So again, I did not originally architect our React Native app (but solely built the back-end). And I had my hands all over the front-end apps (mobile and web) fixing bugs and adding features or finishing features to the so that my devs could move on to scaffolding out more boilerplate and styles for new screens/features (to meet our schedule constraints).

For instance, I worked a lot with the Map and Nativebase Card Swiper. Initially I had other developers scaffold our boilerplate for those pages and do the initial integration of the 3rd party components, which was typically the easy part for them. Obviously copy/pasting boilerplate shouldn't have been difficult - but for the other developers besides the original architect it was hard for some reason - so I often was correcting boilerplate code to get things working. The 3rd party components we used were typically super easy to just stick into our project, but getting them to do exactly what we wanted them to do was typically a more involved process, which is what I'd ended up doing a lot of.

Again I worked across the entire app and architected the back-end. The only area I would say I'm least confident in currently is 'originating' styles. Honestly I'm also not the best at 'originating' styles in CSS either. Typically I like to take an existing design (including styles) and port them over for new features etc. Its just not my strong suit. I helped my other developers find a process for translating our PSD designs from Photoshop to React Native styling for components, but I never personally touched that.

*(Honestly, you can outsource that work for dirt cheap... or train your designers to build designs on a platform that can export directly to React Native styles or CSS for that matter. There are lots out there, and they are focused on designers not engineers/programmers. It's my personal opinion you should NOT be spending money on engineers/programmers building styles... I think its wasteful - ie. robots can do that for pennies, if you plan correctly... and off the soapbox...)*

I did end up modifying styles to help things look better or again, port over styles for new scenes/pages but I did not initially build our styles from scratch. I understand React Native styling (and CSS for that matter) and once I have a baseline, changing style to get certain effects is no problem. I'm just not really a one for initially designing UX/UI, etc. I do feel I have an eye for when something looks good or not though.

#### React Native Maps Features

So for the map, after the initial bootstrap of that scene - some of the problems we ran into that I resolved was (1) the actual native library had bugs in iOS and worked differently in Android vs iOS - so I opted to switch the iOS configuration to use Google maps so that both apps had a unified map across Android and iOS. Then (2) there was also another issue in iOS where specifically on Google maps the map pins would render in a way where the library acted like you were moving a set of pins to a new set of locations every time the screen refreshed, but actually we were just redrawing the exact same state of pin positions - which was a known library bug with Google Maps and iOS at the time. I opted to build a workaround where I controlled when we allowed the pins to be redrawn separately from the rest of the scene/page. Fixing the actual library on the Native side would have been ideal, but I didn't have time to go that indepth into the problem for this project.

#### NativeBase Card Swiper Features

For the card swiper, the issue that my dev had was that the card swiper was built to really only have 2 choices yes/no, but we needed a third choice of "maybe". The idea was that a recruiter would be looking at a set of athletes from a school and either be interested in following them, never want to see them again, or defer that decision. Also the backend needed to be updated to handle 'bookmarking' the 'yes', 'maybe' and 'no' responses to impact future searches.

The client also wanted the card swiper to move to the next set of athletes of the next school displayed on the map once the cards ran out. Another issue my dev had was the component broke when you ran out of cards, which required a restart of the app. Also there were state issues with the card swiper when exiting the one set of athletes and activating the feature for another set. In general, it was just really buggy.  I had to get it working right, so I could have my dev start a new feature and advance our schedule.

So my dev built the boilerplate (which in this case was mostly just a component screen with a Nativebase 3rd party component) and loaded an initial set of athletes to start discovering those issues - and then I took over enhanced it found more bugs and eventually got it full feature complete.

#### Components Built from Scratch (ie. On Top of FlatLists)

The components I built the most from scratch were (1) the scene where you could see/manage all the athletes you bookmarked, and (2) the saved search feature. 

Both pages were variations of mostly a flatlist. The manage page with the athlete's information and a couple buttons to navigate to their details screen or remove them from the list, and the saved search which listed search configurations the user saved from the map. I mention flatlist because that was another performance issue we discovered, which is obvious when reading the docs - that you want to use flatlists for lists longer sets of data because the rendering of the elements are more optimized.

#### React Native => Web App Port (ReactXP)

Lastly we ported the entire app to ReactJS using a microsoft library called [ReactXP](https://microsoft.github.io/reactxp/). The gotcha here was that we had to (1) refactor the entire app to use ReactXP components which replaced standard React Native components, and the second gotcha (2) was probably finding the right webpack configuration among varying documentation. 

I solved the webpack issues simply by creating a new react project where my dev was trying to get a ReactXP github sample to work. I had that other dev do a majority of the 'boilerplate' mapping and refactoring React Native components to ReactXP. Then I came in after him and spent a day just getting his refactor to run on the web (he literally just was replacing code and couldn't get it to run at all even with webpack solved, I believe).

After I got it running on web, I went through and applied the same refactoring logic (and some other changes) to get things he missed showing up correctly (again, he couldn't see what he was changing). At that point we stopped working on the Web App port, leaving it in more of a rough proof of concept React Native code to ReactJS unified code base (ie. with ReactXP literally the same code base could compiled for mobile and web). The styling was not updated to look better on larger desktop viewports, and we didn't refactor a number of the native components that would need to be built from scratch or replaced with web equivalents. The client decided not to more forward with the web version of the app, and opted to do more functionality on the mobile app.

## Screenshots

### Registration Page (Android)
![](https://bretroyster.siterubix.com/wp-content/uploads/2019/01/2018-09-26_1405.png?raw=true)

### Athlete Details Page
![](https://bretroyster.siterubix.com/wp-content/uploads/2019/01/2018-09-26_1409.png?raw=true)

### Map View Page
![](https://bretroyster.siterubix.com/wp-content/uploads/2019/01/2018-09-26_1409_001.png?raw=true)

### Map View UI options
![](https://bretroyster.siterubix.com/wp-content/uploads/2019/01/2018-09-26_1410.png?raw=true)

### Search Dialog
![](https://bretroyster.siterubix.com/wp-content/uploads/2019/01/2018-09-26_1410_001.png?raw=true)

### Evaluate Athlete Page (NativeBase Card Swiper)
![](https://bretroyster.siterubix.com/wp-content/uploads/2019/01/2018-09-26_1411.png?raw=true)

### Map Filter Page
![](https://bretroyster.siterubix.com/wp-content/uploads/2019/01/2018-09-26_1411_001.png?raw=true)

### Saved Search Page
![](https://bretroyster.siterubix.com/wp-content/uploads/2019/01/2018-09-26_1412.png?raw=true)

### Athlete Board Page (Android)
![](https://bretroyster.siterubix.com/wp-content/uploads/2019/01/2018-09-26_1408.png?raw=true)

### Login page
![](https://bretroyster.siterubix.com/wp-content/uploads/2019/01/2018-09-26_1404.png?raw=true)
