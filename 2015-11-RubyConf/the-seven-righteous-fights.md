#7fights
@wiredferret

The Seven Righteous Fights
(you should be arguing)

About failures

We all have ruts in our programming
Need to understand all stages: green, mid, brown

Compound interest is terrible with technical debt

# do not hand code labels, use internationalization
things to do:
* make labels refer to lists
* avoid putting words in images
* do not use screen captures for training
* build in support for extended characters (users should be able to enter their name)

# Security
Eventually you will be found by a malicous person, so have security
Security is neither cheap nor easy but it is important
* hire someone who knows security, at least as consulatant
* AUTHENTICATION is not AUTHORIZATION is not SECURITY
* leave room for encryption (use https & encryption)
* know what kind of data you are redacting and what kind of meta data is revealing (not just names and ssn)
* only collect data you actually need (i.e. gender)
* allow deletion of users (true deletion) make removal after time a default
* use whitelist security for scripts needed (kill ad scripting)
* Do not recreate the wheel (use AD, open id, etc)
* Stop saying that word.. secure

# Extensibility
Ability to play nice with others
* Make clean and nice APIs, even for internal APIs
* Make API like Legos

# Documentation
* documents should be more useful than Stack Overflow
* secrets are actually the business model and should be publically available
* documentation is subtle self promotion
* onboarding w/o documentaion is a huge tax on senior developers
* secretive build engineers are BAD build engineers
* release notes are "the one type of documenation that will be read" do them
* document your coding intent (why is the software?)

# Affordance
What your software is trying to get people to do, and how easy it is
* make the correct path, the easy path
* make sure it works without admin level security (is it still easy to do?)
* make software that is like auto-savings, give benefit without any user effort
* you think you are going to go back and fix it, but you are not
    * even if you do, users will be used to it and angry you changed it

# Acceptance
Find a group of actual users and talk to them
* five users and a web x session will change your world
* do not tell the user anything, shut up and observe
* 1,3,2 UX should be a priority (if you cannot hire an expert, become a student)
    * Kathy Sierra book, Bad Ass

# Accessability
Have you looked at software with your glasses off, can you see it?
* Check your UI w/o glasses and w/o high definition screen
* Check it on an actual phone (the phone your dad uses)
* 8% of men are r/g colorblind.  make sure it does not rely on color
* do not use "click here" because screen readers will be lost
* not everyone has broadband, be considerate
* do not forget those that use older phones
* we are all only temporarily able bodied

How to fit all this into project timelines? Can we afford not to?

* Write a coding style guideline and follow it
* brown bag lunches to talk about it
* pair programming with best practices
* add tests for accessability and usability
* cultivate diversity and representation into you team
* ask questions

Software has to be (section 508) ADA compliant to get federal funding including colleges, prisons and hospitals

## Be productively lazy
Optimize as much as possible on the front end to do less on the back end.

