---
layout: post
title:      "Jumping Into Heroku Taught Me A Lesson..."
date:       2018-10-04 13:05:04 +0000
permalink:  jumping_into_heroku_taught_me_a_lesson
---


And that lesson is "Never stop using the skills you were taught." It's been a year since I finished the Full-Stack course with Learn.co. Since that time, I've been working as a Software Support Engineer focused primarily on fixing bugs in a company's Rails backend. I loved React when I worked with it to create a project and was hoping to use it right out of school. That didn't happen. Instead, my frontend work consisted purely of HTML/CSS, ERB, and HAML.
Long story short, I learned a very valuable lesson when trying to launch my React/Rails API app in Heroku this week. That is that React got a complete rewrite. I've been spending these morning hours seeing if the rewrite was minor enough for me to inject the recommended changes into my pre-exisiting app and make it work. So far...not so much. For the errors that npm was throwing, I eliminated all that were tied to my actual code. All that's left were those tied to the nodes themselves.

....

It's been a few hours and I'm happy to report that I've got the website loading and the store functioning. My only issue left is to figure out why my links aren't working with React's new **BrowserRouter** tool. When I find out, it'll go here. But just to share the code that doesn't seem working:

```
export const Routes = (store) => (
	<AlertProvider template={AlertTemplate} {...alertOptions}>	                                 
	  <BrowserRouter>
		  <Switch>
			  <Route path="/" component={App}/>
			  <Route path="/search" component={GoogSearch}>
		      	<Route path="/search/:id" component={ImageAdd}/>
			  </Route>
			  <Route path="/tags" component={TagSplash}/>
		  </Switch>
	  </BrowserRouter>
	</AlertProvider>
);
```

And remember, don't be lazy like I was. 
