# College Football Recruiting App (Code Samples & Screenshots)
This is code samples and screenshots from a private college football recruiting demo I worked on. 

The logo and name has been altered for anonymity. To my knowledge, this app never launched.

Work Summary
---

Mobile Development: android studio, apple xcode, google maps api, redux, redux-saga, react-native

Startup client needed MVP of iOS and Android mobile apps for next round of investor fund-raising efforts.

I lead a team of 2 front-end developers and myself as a senior full-stack developer.

I was responsible for developing (1) all the front-end mapping features and (2) the entire Java / Spring Boot back-end server. 

Also finished and refined majority of front-end development started by other teammates, which was necessary to shorten our integration/QA cycle to help meet client's cost constraints.

Solely responsible for production-ready testing, debugging and fixing features prior to build releases. 

Created and maintained scripts for build and dev environments. 

Solely responsible for weekly builds in xCode and Android Studio, and deploys to iTunesConnect (Apple App Store and Test Flight) and Play Store respectively.

Client was very happy with overall outcome, and received an overwhelmingly positive response from their current investors.

**NOTE:** Client company logo and name have been replaced in screen shots to maintain privacy. 

Registration Page (Android)
--
![](https://bretroyster.siterubix.com/wp-content/uploads/2019/01/2018-09-26_1405.png?raw=true)

My React / React Native Experience on this Project (brain dump)
---

We had a new client that needed a college recruiting app created in iOS, Android, and web in roughly that priority.

After some discussion, it seemed like it was time to break into React Native.

From an architecture standpoint, I initially built the backend for our RN project with using a JHipster stack which is Spring Boot (Java), AngularJS as an admin interface (I opted not to use a React front-end simply because we were new to React and I wanted to keep that learning complexity directed at the app and not the admin interface).

After establishing the back-end, my co-worker had settled on the majority of the architecture for the react native app, which consisted of a fairly large but complete boilerplate of "screens" and "components" (or smart and dumb components - our 'screens' held state and our components did not).

When I jumped into the React development I used https://reactnativeexpress.com to spin up, which was super helpful. And spent a couple hours with my co-worker on the phone to get an understanding of his 'boilerplate'.

The state management was 'mostly' react redux, for forms I opted to use the standard react state logic (and I instructed our team to do the same) - because I personally didn't see the benefit in all of the boilerplate overhead of redux for the form inputs AND I felt like it created a nice separation of intent - react state was used in very temporarily circumstances and react redux was indented for everything else.

I looked into how easy it was to add redux persist to our architecture, but by the time I discovered it I didn't have time to confidently test it in that app and ensure it didn't have some kind of adverse effect that would create more cost for our customer - and it wasn't immediately needed either, even though it was really interesting to me.

This is a good time to mention, that this project was a client project and our client was very concerned with speed/cost and we didn't really have time to do things that didn't have an immediate and direct benefit that the client was specifically asking for - most of my projects in my previous role were like that - even though sometimes I did find time to 'experiment' if I knew the risk was worth it. Redux persist, could have been marginally worth it - just too many unknowns for that time of that project when I was operating us at very low risk.

Anyway... We also used Redux-Saga for our HTTP connections to the back-end spring boot server I developed. Honestly, after being exposed to an alternative HTTP client approach in React - Redux-Saga could feel possibly boilerplate 'heavy', but I would still use it because I think it enforces a clear pattern working with HTTP with redux.

One of the bigger, gotchas that happened on this project was discovering that (for some reason) react-navigation created terrible memory performance issues in Android for apps with larger sets of scenes/pages. So I was also exposed to React Native Navigation by Wix which I thought was fairly straightforward to work with (but obviously that doesn't really apply to ReactJS) - another challenge of that project was library integration like React Native Maps and working with Expo (ie. trying to circumvent their constraints while still wanting to leverage their tools - eventually opting to just leave Expo completely because it was it was too much work to attempt to circumvent some of their architecture - and it was also a decision above my head)

Also leveraged open-source components like NativeBase, and one other component library that I cant recall right now. I used them for a card swiper and tabs.

So again, I did not originally architect our react native app. But I had my hands all over it fixing bugs and adding features or finishing features that my other devs couldn't get completed on a timely schedule. For instance, I worked a lot with the Map and Card swiper. Initially I had other develops copy/paste our boilerplate for those pages and do the initial integration and styling of the 3rd party components, which was typically the easy part for them. Obviously copy/pasting boilerplate shouldn't have been difficult - but for everyone but the original dev it was for some reason - so I often was correctly incorrect boilerplate code to get things working. The 3rd party component we used were typically super easy to just stick into our project, but getting them to do exactly what we wanted them to do was typically a more involved process, which is what I'd ended up doing most of.

So I hope I'm indicating that I was exposed to work across the entire app because that was really the case. The only area I would say I'm least confident in currently is in styling. Honestly I'm also not the best at CSS either. Typically I like to take an existing design (including styles) and port them over of new features etc. Its just not my strong suit. I helped my other developers find a process for translating PSDs from Photoshop to React Native styling for components, but I never personally touched that. I did end up modifying styles to help things look better or again, port over styles for new scenes/pages but I did not initially build and styles for scratch.

So for the map, after the initial bootstrap of that scene - some of the problem we ran into that I resolved was (1) the actual native library had bugs in iOS and worked differently in Android vs iOS - so I opted to switch the iOS to use Google maps so that both were unified and worked closer to the same. Then (2) there was also another issue in iOS where specifically on Google maps the map pins would render in a way were the library acted like you were moving a set of pins to a new set of locations, but actually we were just redrawing the same page - which was a know library bug. I opted to build a workaround where I controlled when we redrew the pins separately from the rest of the scene/page. Fixing the actual library on the Native side would have been ideal, but I didn't have time for that on this project.

For the card swiper, the issue that my dev had was that the card swiper was built to really only have 2 choices yes/no, but we needed a third choice of "maybe". The idea was that a recruiter would be looking at a set of athletes from a school and either be interested in following them, never want to see them again, or defer that decision. Also the backend needed to be updated to handle 'bookmarking' the 'yes' and 'maybe' responses to show up in the future and 'no' responses to not show up in their searches anymore. The client also wanted the card swiper to move to the next set of athletes of a different school once the cards ran out. Another issue my dev had was the component broke when you ran out of cards and you would be stuck on that page and need to restart the app. I had to fix all that stuff to work right. So my dev built the boilerplate (which in this case was mostly just a component screen with a Nativebase 3rd party component) and loaded an initial set of athletes and discovered those issues - and I had to make the rest of it work.

The component I built the most from scratch was the scene where you could see all the athletes you bookmarked. It was a flatlist with the athlete's information and a couple buttons to navigate to their details screen or remove them from the list. I mention flatlist because that was another performance issue we discovered, which is obvious when reading the docs - that you want to use flatlists for lists longer sets of data because the rendering of the elements are more optimized.

Lastly we ported the entire app to ReactJS using a microsoft library called ReactXP. The gotcha here was that we had to refactor the entire app to use ReactXP components which replaced standard React Native components, and the second gotcha was probably finding the right configuration webpack configuration among varying documentation. I solved the webpack issues simply by creating a new react project where my dev was trying to get a ReactXP github sample to work. I had the other dev do a majority of the 'boilerplate' mapping and refactoring React Native components to ReactXP. Then I came in after him and spent a day just getting his refactor to run on the web (he literally just was replacing code and couldn't get it to run at all) and after it was running I went through and applied the same refactoring logic to get things he missed to show up correctly. In that case we stoped the webapp at a more rough demo stage. The client decided not to move forward with styling updates to make it look better for larger viewports then mobile sizes. Plus like the map and other native components like the card swiper (I think - the map for sure) would need to be build from scratch or replaced with alternative web components.

That concludes a majority of my React/React Native experience with this project.
