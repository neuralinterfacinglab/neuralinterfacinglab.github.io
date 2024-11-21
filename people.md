---
title: People
permalink: /people/
---


### Meet The Team!
<img style=" width:100%;" src="{{site.baseurl}}\images\people\IMG_7385.jpg" data-action="zoom">

<hr>


{% assign people_sorted = site.people | sort: 'joined' %}
{% assign role_array = "pi|postdoc|gradstudent|researchstaff|visiting|others|alumni" | split: "|" %}

{% for role in role_array %}

{% assign people_in_role = people_sorted | where: 'position', role %}

<!-- Skip section if there's nobody -->
{% if people_in_role.size == 0 %}
  {% continue %}
{% endif %}

<div class="pos_header">
{% if role == 'postdoc' %}
<h3>Postdoctoral Fellows</h3>
 {% elsif role == 'pi' %}
<h3>Principal Investigators</h3>
 {% elsif role == 'gradstudent' %}
<h3>PhD Students</h3>
 {% elsif role == 'researchstaff' %}
<h3>Research Staff</h3>
 {% elsif role == 'visiting' %}
<h3>Visiting Scholars</h3>
 {% elsif role == 'others' %}
<h3>Honorary Members</h3>
 {% elsif role == 'alumni' %}
<h3>Alumni</h3>
{% endif %}
</div>

{% if role != 'alumni' %}
<div class="content list people">
  {% for profile in people_sorted %}
    {% if profile.position contains role %}
      <div class="list-item-people">
        <p class="list-post-title">
          {% if profile.avatar %}
            <a href="{{ site.baseurl }}{{ profile.url }}"><img class="profile-thumbnail" src="{{site.baseurl}}/images/people/{{profile.avatar}}"></a>
          {% else %}
            <a href="{{ site.baseurl }}{{ profile.url }}"><img class="profile-thumbnail" src="http://evansheline.com/wp-content/uploads/2011/02/facebook-Storm-Trooper.jpg"></a>
          {% endif %}
          <a class="name" href="{{ site.baseurl }}{{ profile.url }}">{{ profile.name }}</a>
        </p>
      </div>    
    {% endif %}
  {% endfor %}
</div>
<hr>

{% else %}

<br>

| Who are they | When were they here | Where they went |
| :------------- |:-------------| :-----------|
| Maarten Ottenhoff | PhD Student (2020 -  2024)| PostDoc at Brown |
| Berkhan Genc | Visiting Scholar 2023 | PhD Student at UM |
| [Laura Marras](https://www.imtlucca.it/it/laura.marras) | Research Assistant (2021 - 2022) | PhD student @ IMT Lucca, Italy
| [Jeroen Habets](https://www.linkedin.com/in/jeroen-habets-b6721321/) | PhD Student (2017 - 2021) | Scientific consultant RuneLabs & Postdoc Neurosurgery Charité |
| Jeremy Saal | Research Assistant (2019 - 2020) | PhD student @ UCSF |
| [Jonas Kohler](https://ch.linkedin.com/in/jonasmoritzkohler) | Visiting Researcher (2020) | Researcher @ Oculus |

{% endif %}
{% endfor %}
