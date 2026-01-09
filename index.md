---
layout: default
title: Home
---
<section class="container my-5">
  <div class="row align-items-center">
    <div class="col-md-5">
      <img src="/img/ErinMackeyHeadshot1.jpg" class="img-fluid rounded shadow" alt="Erin Mackey Headshot">
    </div>
    <div class="col-md-7">
      <h1 class="display-4" id="about">Erin Mackey</h1>
      <p class="lead">Actor | Artist | Performer</p>
      <p>{{site.data.bio.text}}</p>
      <a href="https://drive.google.com/file/d/1R_P7b3K12tAYCfJnNhoGDQp-rV2IEf2-/view?usp=sharing"  target="_blank" class="btn btn-outline-dark">Download Full Resume (PDF)</a>
    </div>
  </div>
</section>

<section class="container my-5" id="resume">
  <h2 class="mb-4">Credits</h2>
  
  {% for section in site.data.credits %}
  <h3 class="h5 mt-4 text-uppercase text-muted">{{ section.category }}</h3>
  <table class="table table-hover">
    <thead class="table-light">
      <tr>
        <th class="col-4">Production</th>
        <th class="col-3">Role</th>
        <th class="col-3">Company/Network</th>
		<th class="col-1">Year</th>
      </tr>
    </thead>
    <tbody>
      {% for item in section.roles %}
      <tr>
        <td><strong>{{ item.show }}</strong></td>
        <td>{{ item.role }}</td>
        <td>{{ item.company }}</td>
		<td>{{ item.date | date: "%Y" }}</td>
      </tr>
      {% endfor %}
    </tbody>
  </table>
  {% endfor %}
</section>

<section class="container my-5" id="education">
  <h2 class="mb-4">Education / Training</h2>
  
  <table class="table table-hover">    
    <tbody>
      {% for item in site.data.education %}
      <tr>
        <td><strong>{{ item.course }}</strong></td>
        <td>{{ item.location }}</td>
        <td>{{ item.instructor }}</td>
		<td>{{ item.date | date: "%Y" }}</td>
      </tr>
      {% endfor %}
    </tbody>
  </table>
</section>

<section class="container my-5 bg-light p-4 rounded">
  <h3>Special Skills</h3>
  <div class="row">
    <div class="col-md-4">
      <strong>Languages/Accents</strong>
      <p>Standard American, Canadian</p>
    </div>
    <div class="col-md-4">
      <strong>Voice</strong>
      <p>Mezzo-Soprano</p>
    </div>
    <div class="col-md-4">
      <strong>Dance</strong>
      <p>Acro, Ballet, Ballroom, Contemporary, Jazz, Latin, Roller Dance, Tap, Tumbling</p>
    </div>
    <div class="col-md-4">
      <strong>Sports</strong>
      <p>Baseball, Billiards, Cycling, Golf, Roller Skating, Softball, Swimming, Tennis</p>
    </div>
    <div class="col-md-4">
      <strong>Other</strong>
      <p>Driver's License (class 5), Motorcycle License (class 6), seamstress/tailor</p>
    </div>
  </div>
</section>

<section class="container my-5" id="gallery">
  <h2 class="mb-4">Gallery</h2>
  <div class="row g-3">
	  {% assign gallery_files = site.static_files | where_exp: "file", "file.path contains 'assets/images/gallery'" | sort: "path" | reverse %}
		
		{% for file in gallery_files %}
		  {% if file.extname == ".jpg" or file.extname == ".png" or file.extname == ".jpeg" or file.extname == ".webp" %}
		  <div class="col-6 col-md-4 col-lg-3">
			<a href="#" data-bs-toggle="modal" data-bs-target="#imageModal" onclick="updateModal('{{ file.path | relative_url }}')">
			  <img src="{{ file.path | relative_url }}" class="img-fluid rounded shadow-sm gallery-thumb" alt="Gallery Image">
			</a>
		  </div>
		  {% endif %}
		{% endfor %}
    
    </div>
</section>

<div class="modal fade" id="imageModal" tabindex="-1" aria-hidden="true">
  <div class="modal-dialog modal-dialog-centered modal-lg">
    <div class="modal-content bg-transparent border-0">
      <div class="modal-body p-0 text-end">
        <button type="button" class="btn-close btn-close-white mb-2" data-bs-dismiss="modal" aria-label="Close"></button>
        <img src="" id="modalImage" class="img-fluid rounded" alt="Zoomed View">
      </div>
    </div>
  </div>
</div>

<section class="container my-5" id="contact">
  <div class="row justify-content-center">
    <div class="col-md-8 col-lg-6">
      <div class="card shadow-sm">
        <div class="card-body p-4">
          <h2 class="text-center mb-4">Contact Erin</h2>
          <div class="text-center mb-4">
			  <p class="text-muted small uppercase fw-bold">Find me on</p>
			  <div class="d-flex justify-content-center gap-3">
				{% for link in site.data.social %}
				<a href="{{ link.url }}" target="_blank" class="btn btn-outline-dark btn-sm shadow-sm">
				  <i class="bi {{ link.icon }} me-1"></i> {{ link.name }}
				</a>
				{% endfor %}
			  </div>
			</div>
			<hr class="my-4">
          <form action="https://formspree.io/f/mreezzrw" method="POST">
            <div class="mb-3">
              <label for="name" class="form-label">Name</label>
              <input type="text" name="name" class="form-control" id="name" required>
            </div>
            
            <div class="mb-3">
              <label for="email" class="form-label">Email Address</label>
              <input type="email" name="_replyto" class="form-control" id="email" required>
            </div>

            <div class="mb-3">
              <label for="subject" class="form-label">Subject</label>
              <select name="subject" class="form-select">
                <option value="Booking Inquiry">Booking Inquiry</option>
                <option value="Audition Request">Audition Request</option>
                <option value="General Inquiry">General Inquiry</option>
              </select>
            </div>

            <div class="mb-3">
              <label for="message" class="form-label">Message</label>
              <textarea name="message" class="form-control" id="message" rows="5" required></textarea>
            </div>

            <input type="text" name="_gotcha" style="display:none" />

            <div class="d-grid">
              <button type="submit" class="btn btn-dark btn-lg">Send Message</button>
            </div>
          </form>
          
        </div>
      </div>
    </div>
  </div>
</section>