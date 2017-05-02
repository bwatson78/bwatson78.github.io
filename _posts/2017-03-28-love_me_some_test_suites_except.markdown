---
layout: post
title:  "Love Me Some Test Suites, Except..."
date:   2017-03-28 18:07:16 +0000
---


So far, throughout the course, the testing suites used have been godsends. There is not a better way to learn Ruby then RSPEC telling you can see what's failing. Capybara even increases the readability of a web application, thus making it easier (and blunter) what broke. Even in Javascript land, Mocha is quite descriptive with what needs to be fixed.
But when AJAX came around, things got really confusing, because Webmock is in play. Here's an example of a Webmock error:


 ```
 1) External request queries FactoryGirl contributors on GitHub
     Failure/Error: response = Net::HTTP.get(uri)
     WebMock::NetConnectNotAllowedError:
       Real HTTP connections are disabled.
       Unregistered request: GET https://api.github.com/repos/thoughtbot/factory_girl/contributors
       with headers {
         'Accept'=>'*/*',
         'Accept-Encoding'=>'gzip;q=1.0,deflate;q=0.6,identity;q=0.3',
         'Host'=>'api.github.com',
         'User-Agent'=>'Ruby'
       }

       You can stub this request with the following snippet:

       stub_request(:get,     "https://api.github.com/repos/thoughtbot/factory_girl/contributors").
     with(:headers => {'Accept'=>'*/*', 'Accept-Encoding'=>'gzip;q=1.0,deflate;q=0.6,identity;q=0.3', 'Host'=>'api.github.com', 'User-Agent'=>'Ruby'}).
     to_return(:status => 200, :body => "", :headers => {})

       ============================================================
     # ./spec/features/external_request_spec.rb:8:in `block (2 levels) in <top (required)>'

Finished in 0.00499 seconds
1 example, 1 failure
```

As a student seeing that the first time, especially one accustomed to the friendlier test suites like Mocha, RSPEC, and Capybara, fear creeps in.
The main reason, I believe, that more people don't become programmers is that they're learning a different language. The term, "It's all Greek to me," is said to me by friends and family anytime they look over my shoulder at code. The difference is that I know that they could grasp it if they realize it's mostly shorthand. If you know that a "fax" is shorthand for "facsimile," then you can get comfortable with ```var``` representing variable and ```def``` replacing define. I think that the writers of RSPEC, Mocha, and Capybara--hell! even the creator of Ruby know that, in order for there to see progress in what computers can do, more people need to feel invited by the simplicity of the process. I know that, even with 5 years under my belt, I'm not going to write the next big application that will change the world. I will, most likely, just start feeling comfortable with the syntax and contributing to the community. That error snippet up there is what newbs fear the most. If we saw that test result first, we'd walk away. Since I've worked with three or four other suites before, I can start to search for what the results are saying--but I still haven't figured it out.
Other suites bring up expectations--your application breaks because a method written as such:

```
def addition(num1, num2)

num1 + num2

end
```

doesn't return 2 when ```num1``` and ```num2``` both equal 1. The test suite actually states that it was expecting 2. Where in the above Webmock snippet does it say that? This code:

```
You can stub this request with the following snippet:

       stub_request(:get,     "https://api.github.com/repos/thoughtbot/factory_girl/contributors").
     with(:headers => {'Accept'=>'*/*', 'Accept-Encoding'=>'gzip;q=1.0,deflate;q=0.6,identity;q=0.3', 'Host'=>'api.github.com', 'User-Agent'=>'Ruby'}).
     to_return(:status => 200, :body => "", :headers => {})
```

is especially maddening. I would presume that that response would be giving you a clue. It isn't. It is fundamentally the same as the "Unregistered request." The best thing this test suite does is to reinforce what most instructors drill into their students on Learn: "read the tests." With the previous suites, at least for me, that hasn't been required. Their test results spit out their expectations. Webmock doesn't. 

I know that I'm near the end of the course and things always get harder at the end. This is more of a wakeup call to those students not near my point in the course. It's not meant to scare you at all. Just "read the tests."
