---
layout: page
title: Spring 2025
---

{% assign team = site.data.team_spring25 | sort : "name" %}

### Instructors

<div class="clearfix">
{% for people in team %} 
    {% if people.type == "PI" %} 
        {% include avatar_entry.html %} 
    {% endif %} 
{% endfor %}
</div>

### Teaching Assistants
<div class="clearfix">
{% for people in team %} 
    {% if people.type == "TA" %} 
        {% include avatar_entry.html %} 
    {% endif %} 
{% endfor %}
</div>

### Course Schedule

Lecture: Mon, Wen 12:30-13:50, MSE 103

Lab: Tue 18:00-20:50 (Sec. 1), 18:00-20:50 (Sec. 2), WCH 127

<iframe style="width:100%; height:600px; overflow:hidden" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQfqGBv6sXs_6Q9PaJzMf6tCFA90NeOQCxhH4m7xBlvfBIcmuoasMAUZlAxFb1VgJZxBPg4U5nkIxq3/pubhtml?gid=0&amp;single=true&amp;widget=false&amp;range=A1:F21&amp;headers=false"></iframe>

### Labs and Final Project
Students form into teams of three (3) to finish the labs and the final project using Meta Quest.

- Lab 1: Unity Basics
- Lab 2: VR Mirror
- Final Project: Design an AR/VR/MR/XR application

### Selected Final Project Demos
{% assign project = site.data.team_spring25_project | sort : "name" %}
<div class="clearfix">
<br>
{% for p in project %}
    <div class="videos">
        {% if p.web %}
            <h3><a href="{{ p.web }}" target="_blank">{{ p.name }}</a></h3> 
        {% else %}
            <h3>{{ p.name }}</h3> 
        {% endif %}
        {% comment %} Extract YouTube video ID from various YouTube URL formats {% endcomment %}
        {% assign youtube_id = '' %}
        {% if p.video contains 'youtu.be/' %}
            {% assign youtube_id = p.video | split: 'youtu.be/' | last | split: '?' | first %}
        {% elsif p.video contains 'youtube.com/watch?v=' %}
            {% assign youtube_id = p.video | split: 'v=' | last | split: '&' | first %}
        {% elsif p.video contains 'youtube.com/embed/' %}
            {% assign youtube_id = p.video | split: 'embed/' | last | split: '?' | first %}
        {% endif %}
        
        {% if youtube_id != '' %}
            <iframe width="640" height="360" src="https://www.youtube.com/embed/{{ youtube_id }}" frameborder="0" allowfullscreen></iframe>
        {% else %}
            <video width="640" height="360" controls>
                <source src="{{p.video}}" type="video/mp4">
            </video>
        {% endif %}
    </div>
{% endfor %}
</div>