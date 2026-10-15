<template>
  <div class="contact-page">
    <div class="contact-header">
      <h1>Contact Us</h1>

      <p>
        We'd love to hear from you. Please fill out the
        form below or reach out via our contact info.
      </p>
    </div>

    <div class="contact-content">
      <div class="contact-info">
        <div class="info-item">
          <div class="info-icon">📍</div>

          <div>
            <h3>Our Office</h3>
            <p>123 Event Street, Tech City, 10101</p>
          </div>
        </div>

        <div class="info-item">
          <div class="info-icon">📞</div>

          <div>
            <h3>Phone</h3>
            <p>+62 812 3456 7890</p>
          </div>
        </div>

        <div class="info-item">
          <div class="info-icon">✉️</div>

          <div>
            <h3>Email</h3>
            <p>hello@gatherly.com</p>
          </div>
        </div>
      </div>

      <form class="contact-form">
        <div class="form-group">
          <label>Name</label>
          <input
            type="text"
            class="form-control"
          />
        </div>

        <div class="form-group">
          <label>Email</label>
          <input
            type="email"
            class="form-control"
          />
        </div>

        <div class="form-group">
          <label>Message</label>

          <textarea
            class="form-control"
            rows="5"
          ></textarea>
        </div>

        <button
          type="submit"
          class="btn-submit"
        >
          Send Message
        </button>
      </form>
    </div>
  </div>
</template>