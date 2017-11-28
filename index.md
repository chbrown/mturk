---
layout: default
title: Overview
summary: Overview of terminology, useful links, prerequisites, and site layout.
# date: 2017-11-27
---

The official introduction can be found on the [Amazon website](https://docs.aws.amazon.com/AWSMechTurk/latest/AWSMechanicalTurkRequester/IntroductionArticle.html).

The instructions and tips & tricks on this site are intended as concise and practical advice to kick-start custom solutions using the Amazon Mechanical Turk platform.


### Terminology

- **AMT**:
  <b>A</b>mazon <b>M</b>echanical <b>T</b>urk
- **Requester**:
  You, the experimenter, i.e., the person paying money for other people's time.
- **HIT**:
  The <b>H</b>uman <b>I</b>ntelligence <b>T</b>ask of your creation.
  Technically, this refers to a small static part of a larger job (a **HIT Type**),
  but is colloquially used to refer all types of jobs / experiments / tasks on AMT.
- **Turker** / **Worker**:
  The subject of your experiment or task, optimally a real person
- **Sandbox**:
  The AMT staging area.
  + No one pays or gets paid to work on sandbox HITs;
    the sandbox exists solely to test out the HITs you've created before you submit them to the production site.
  + You always have $10,000 USD in the sandbox.


### Quicklinks

AMT is located at four different websites:

<table class="grid">
  <thead>
    <tr>
      <th></th>
      <th>Production</th>
      <th>Sandbox</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Requester</th>
      <td>
        <h4><a href="https://requester.mturk.com">Requester site</a></h4>
        For most administrative types of actions outside the API.
      </td>
      <td>
        <h4><a href="https://requestersandbox.mturk.com/">Requester sandbox</a></h4>
        For creating test HITs.
      </td>
    </tr>
    <tr>
      <th>Worker</th>
      <td>
        <h4><a href="https://www.mturk.com/">Worker site</a></h4>
        Which you'll likely never use.
      </td>
      <td>
        <h4><a href="https://workersandbox.mturk.com/">Worker sandbox</a></h4>
        For testing your HIT from the Turker's point of view.
      </td>
    </tr>
  </tbody>
</table>


### Prerequisites

The subsequent pages assume you're familiar with the general workings of AMT.
If you haven't already, go to the requester sandbox and create a simple HIT using AMT's predefined templates.
Then, in the worker sandbox, find that HIT, accept it, work it, and submit it.
Then, back in the requester sandbox, find the submission you just created.


### Site Layout

<ul>
  {% assign sorted_pages = site.pages | sort: 'date' %}
  {% for page in sorted_pages %}
    {% if page.title %}
      <li>
        <h4><a href="{{ page.url | relative_url }}">{{ page.title }}</a></h4>
        {{ page.summary }}
      </li>
    {% endif %}
  {% endfor %}
</ul>
