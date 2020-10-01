---
layout: default
title: Lectures
active_tab: lectures
---

<!-- Create a HTML anchor for the most recent lecture -->
{% assign anchor_created = false %}
{% capture now %}{{'now' | date: '%s'}}{% endcapture %}
<!-- End create a HTML anchor for the most recent lecture -->


<div class="alert alert-info">
You can <a href="">watch recordings of the lecture videos online</a>.
</div>

The lecture schedule will be updated as the term progresses. 

### Week 0 - Pre-course

Please watch this [course overview video](). Also, make sure to fill out the pre-course survey that is available on Courseworks.

Make sure you are registered for the course [Piazza](https://piazza.com/class/kcm2u88of5p1hz), [Gradescope](), and [JupyterHub]().

{% for week in site.data.schedule %}
  <h3>
    {{ week.name }}
  </h3>
  	
 *Textbook Readings:* 	
 <ul style="width:45%; float:left;">
   {% for reading in week.readings %}
      <li><a href="{{ reading.link }}">{{ reading.title }}</a></li>
   {% endfor %}
</ul> 	

*Optional Readings:*
<ul style="width:45%; float:left;">
   {% for reading in week.readings-supp %}
     <li>
   	 {% if reading.authors %}
        {{ reading.authors }}, 
    {% endif %}
          <a href="{{ reading.url }}">{{ reading.title }}</a> 
      </li>
   {% endfor %}
</ul> 	

  	
  	
  <table class="table table-striped">
    <thead>
      <tr>
        <th>Date</th> 
        <th>Topic</th>
        <th>Recordings</th>
        <th>Assignment</th>
      </tr>
    </thead>
    <tbody>

      {% for lecture in week.lectures %}

      <!-- Create a HTML anchor for the most recent lecture -->
      {% capture lecture_date %}{{lecture.date | date: '%s'}}{% endcapture %}
      {% assign lecture_date = lecture_date | plus: 0 %}
      {% assign now = now | minus: 14400 %}

      <tr
      {% if anchor_created != true and lecture_date >= now %}
        {% assign anchor_created = true %}
        id="now" 
      {% endif %}
      
      {% if lecture.type %}
        {% if lecture.type and lecture.type == 'exam' %}
          class="info" 
        {% else if lecture.type and lecture.type == 'deadline' %}
          class="warning"
        {% else if lecture.type and lecture.type == 'no_lecture' %}
          class="success"
        {% endif %}
      {% endif %}
      >

      <!-- End create a HTML anchor for the most recent lecture -->
        <td>{{ lecture.date | date: '%a, %b %-d, %Y' }}</td>
        <td>
           {{ lecture.title }} 


          {% if lecture.slides %}
            <a href="{{ lecture.slides }}">[slides]</a>
          {% endif %}


          {% if lecture.recording %}
            <a href="{{ lecture.recording }}">[video] </a>
          {% endif %}

  	    {% if lecture.speaker %}
            {% if lecture.speaker_url %}
              by <a href="{{ lecture.speaker_url }}">{{ lecture.speaker }}</a> 
            {% else %} 
            by {{ lecture.speaker }}
            {% endif %}
  	    {% endif %}

        </td>
        <td>
          {% if lecture.recordings %}
            {% for assignment in lecture.recordings %}
                {% if assignment.optional %}<b>Optional:</b> {% endif %}
                <a href="{{ assignment.url }}">{{ assignment.title }}</a> 
              <br />
                (Due {{assignment.deadline | date: '%a, %b %-d, %Y' }})
            {% endfor %}
          {% endif %}
        </td>
        <td>
          {% if lecture.assignments %} 
            {% for assignment in lecture.assignments %}
                {% if assignment.optional %}<b>Optional:</b> {% endif %}
                <a href="{{ assignment.url }}">{{ assignment.title }}</a> 
              <br />
                (Due {{assignment.deadline | date: '%a, %b %-d, %Y' }})
            {% endfor %}
          {% endif %}
        </td>
      </tr>
      {% endfor %}
      
    </tbody>
  </table>

  {% endfor %}
