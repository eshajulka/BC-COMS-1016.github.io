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
You can <a href="https://columbia.hosted.panopto.com/Panopto/Pages/Sessions/List.aspx#folderID=%22ad664074-1c72-4e25-9779-ac300135ae05%22">watch recordings of the lecture videos online</a>.
Recordings are saved on Panopto and require a UNI login.
</div>

The lecture schedule will be updated as the term progresses. 

### Week 0 - Pre-course

Make sure to fill out the pre-course survey that is available on Slack.

Make sure you are registered for the course [Gradescope](https://www.gradescope.com/), [JupyterHub](http://jupyterhub.coms1016.barnard.edu/), and [Slack](https://bc-coms-1016-fallb.slack.com/).

{% for week in site.data.schedule %}
  <h3>
    {{ week.name }}
  </h3>
  	
  	
  <table class="table table-striped">
    <thead>
      <tr>
        <th>Date</th> 
        <th>Topic</th>
        <!--<th>Recordings</th>-->
        <th>Reading</th>
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
            {% if lecture.notebook %}
              <br>
              <a href="{{ lecture.notebook }}">[empty notebook]</a>
            {% endif %}
            {% if lecture.completed_notebook %}
              <br>
              <a href="{{ lecture.completed_notebook }}">[completed notebook]</a>
            {% endif %}
            <br>
       

           




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
          {% if lecture.readings %} 	
            {% for reading in lecture.readings %}	
            {% if reading.url %}	
                {% if reading.optional %}<b>Optional:</b> {% endif %}	
                {% if reading.authors %}	
                {{ reading.authors }}, 	
                {% endif %}	
                <a href="{{ reading.url }}">{{ reading.title }}</a> 	
              <br />	
            {% else %}	
                {% if reading.optional %}<b>Optional</b> {% endif %}	
                {% if reading.authors %}	
                {{ reading.authors }}, 	
                {% endif %}	
               {{ reading.title }} 	
              <br />	
            {% endif %}	
            {% endfor %}	
          {% endif %}	
        </td>
        <td>
          {% if lecture.assignments %} 
            {% for assignment in lecture.assignments %}
                {% if assignment.canceled %}<strike> {% endif %}
                {% if assignment.optional %}<b>Optional:</b> {% endif %}
                <a href="{{ assignment.url }}">{{ assignment.title }}</a> 
                (Due {{assignment.deadline | date: '%a, %b %-d, %Y' }})
                {% if assignment.canceled %}</strike> {% endif %}
            <br />
            {% endfor %}
          {% endif %}
        </td>
      </tr>
      {% endfor %}
      
    </tbody>
  </table>

  {% endfor %}
