<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
<form method="GET" action="mailto:msing755@mtroyal.ca" class="p-5">
    <div class="mb-3">
      <label for="name" class="form-label">Full Name</label>
      <input type="text" class="form-control" id="name" name="subject" placeholder="Enter your name" required>
    </div>
    <div class="mb-3">
      <label for="email" class="form-label">Your Email</label>
      <input type="email" class="form-control" id="email" name="body" placeholder="Enter your email" required>
    </div>
    <div class="mb-3">
      <label for="message" class="form-label">Message</label>
      <textarea class="form-control" id="message" name="body" rows="4" placeholder="Your message" required></textarea>
    </div>
    <button type="submit" class="btn btn-primary">Send Email</button>
  </form>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
