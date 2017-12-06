+++
title = "Contact"
comments = false
sharingicons = false
date = 2015-01-01T00:00:00-00:00
+++

Typically I reply within 24 hours if its relevant!

<form action="https://formspree.io/nuhil@nuhil.net"
      method="POST" id="contact-form" novalidate>
  <div class="form-group">
    <input type="email" class="form-control" id="email" name="_replyto" aria-describedby="emailHelp" placeholder="Your email address" required>
    <small id="emailHelp" class="form-text text-muted">I will never share your email with anyone else.</small>
  </div>
  <div class="form-group">
    <textarea class="form-control" id="message" name="message" rows="3" required>Hi Nuhil, </textarea>
  </div>
  <button type="submit" class="btn btn-primary">Send Message</button>
</form>

<script>
  // Example starter JavaScript for disabling form submissions if there are invalid fields
  (function() {
    'use strict';

    window.addEventListener('load', function() {
      var form = document.getElementById('contact-form');
      form.addEventListener('submit', function(event) {
        if (form.checkValidity() === false) {
          event.preventDefault();
          event.stopPropagation();
        }
        form.classList.add('was-validated');
      }, false);
    }, false);
  })();  
</script>
