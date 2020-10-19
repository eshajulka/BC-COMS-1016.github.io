---
title: Intro to Computational Thinking & Data Science - COMS 1016 - Barnard College
layout: default
img: <!-- turk-engraving-detail -->
img_link: <!-- http://en.wikipedia.org/wiki/The_Turk -->
caption: <!--An engraving of the Mechanical Turk, the 18th century chess-playing automaton -->
active_tab: main_page 
---

<i>Data science is the study of extracting value from data</i>. This course will introduce students to the methods and tools used in data science to obtain insights from data. Students will learn how to analyze data arising from real-world phenomena while mastering critical concepts and skills in computer programming and statistical inference. The course will involve hands-on analysis of real-world datasets, including economic data, document collections, geographical data, and social networks. This class is ideal for students looking to increase their digital literacy and expand their use and understanding of computation and data analysis across disciplines. No prior programming or math background is required.

<!-- Display an alert about upcoming homework assignments -->
{% capture now %}{{'now' | date: '%s'}}{% endcapture %}
{% for page in site.pages %}
{% if page.release_date and page.due_date %}
{% capture release_date %}{{page.release_date | date: '%s'}}{% endcapture %}
{% capture due_date %}{{page.due_date | date: '%s'}}{% endcapture %}
{% if release_date < now and due_date >= now %}
<div class="alert alert-info">
<a href="{{page.url}}">{{ page.title }}</a> has been released.  
{% if page.deliverables %}
The assignment has multiple deliverables.
{% for deliverable in page.deliverables %}
The {{deliverable.description}} is due before {{ deliverable.due_date | date: "%I:%M%p" }} on {{ deliverable.due_date | date: "%A, %B %-d, %Y" }}.  
{% endfor %}
{% else %}
It is due before {{ page.due_date | date: "%I:%M%p" }} on {{ page.due_date | date: "%A, %B %-d, %Y" }}.
{% endif %}
</div>
{% endif %}
{% endif %}
{% endfor %}
<!-- End alert for upcoming homework assignments -->


<!--
<div class="alert alert-info" markdown="1">
Check out the [excellent final projects](http://crowdsourcing-class.org/final-projects-2016.html) from last year's class.
</div>
-->


Course number
: [BC COMS](http://cs.barnard.edu/) 1016 - students from all majors are welcome!

Instructor
: [Adam Poliak](http://azpoliak.github.io)

Teaching Assistants
: [Course Staff](staff.html) 

Website 
: [https://coms1016.barnard.edu/](https://coms1016.barnard.edu/)

Discussion Forum
: [Piazza](https://piazza.com/class/kcm2u88of5p1hz)
: [Slack](https://join.slack.com/t/bc-coms-1016-fallb/signup) *Requires signing up via a barnard.edu or columbia.edu email*

Time and place
: Fall B, MTWR 2:40-3:55pm, Location: Check courseworks for Zoom link
: Lab 01 TR 9:00 - 9:50am
: Lab 02 MW 6:10 - 7:00pm

Office Hours
: <a href="office-hours.html">Times</a>

<!--
: Tuesday 6-7pm in 3401 Walnut St, room 452C
: Wednesday 4-6pm in 3401 Walnut Street 4th Floor outside 463C
: Thursday 6-7pm in 3401 Walnut St, room 452C
: Friday 2-4pm in 3401 Walnut Street 4th Floor outside 463C
: CCB's office hours are [by appointment on ccb-office-hours.youcanbook.me](https://ccb-office-hours.youcanbook.me)
-->

Prerequisites
: None - no prior programming or college-math background is required

Modes of Thinking Requirement
: Thinking Quantitatively and Empirically
: Thinking Technologically and Digitally

Course Readings
: Each lecture has an accompanying chapter/section of the [textbook](https://www.inferentialthinking.com/)

Grading
: This is a project-based course. There will be an open book take home midterm but
the majority of your grade will be based on assignments.
* Assignments (Homeworks, mini-projects, Final project) - 70%
* Exams and Quizes (Midterm, Daily Quizes) - 25%
* Participation - 5%

<!--- 
* Homeworks (20%)
* Projects (25%)
* Pre-course quizes (7.5%)
* Midterm (15%)
* Final Project (25%)
* Participation (7.5%)
-->


<!-- old grading 
This is a project-based course.  Instead of exams, you will do a series of hands-on assignments and a final project.  

* Weekly assignments (45%)
* Final project (45%)
* Peer grading (5%)
* Participation (5%)
-->

Late day policy
: To account for issues that arise in these uncertain times, each student has 10 late days for the homeworks and projects.
<br>
See the [Policies](http://localhost:4000/policies.html#late-days) for more details.
<!--
Each student has five free "late days". Homeworks can be submitted at most two days late. If you are out of late days, then you will not be able to submit your homework. One "day" is defined as anytime between 1 second and 24 hours after the homework deadline. The intent of the late day policy it to allow you to take extra time due to unforseen circumstances like illnesses or family emergencies, and for forseeable interruptions like on campus interviewing and religious holidays. You do not need to ask permission to use your late days. No additional late days are granted.
-->

#### Acknowledgments
A Google Cloud Education grant is supporting the computational infrastructure for the course.
<br> 
Eric Van Dusen, his staff, and The Data Science Education Community have been very helpful 
in adopting this course at Barnard. 
