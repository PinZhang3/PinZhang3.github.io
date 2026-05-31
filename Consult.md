---
layout: page
title: Consult
permalink: /consult/
weight: 8
---

<style>
  .contact-wrapper {
    display: flex;
    gap: 60px;
    align-items: flex-start;
    margin-top: 40px;
  }

  .contact-left {
    flex: 1;
  }

  .contact-left .tag {
    display: inline-block;
    border: 1px solid #ddd;
    border-radius: 20px;
    padding: 6px 14px;
    font-size: 14px;
    margin-bottom: 25px;
  }

  .contact-left h1 {
    font-size: 44px;
    line-height: 1.1;
    margin-bottom: 25px;
  }

  .contact-left p {
    font-size: 17px;
    color: #555;
    line-height: 1.5;
  }

  .contact-form-box {
    flex: 1.4;
    border: 1px solid #ddd;
    border-radius: 10px;
    padding: 25px;
    box-shadow: 0 2px 8px rgba(0,0,0,0.05);
  }

  .form-row {
    display: flex;
    gap: 15px;
  }

  .form-group {
    flex: 1;
    margin-bottom: 18px;
  }

  .form-group label {
    display: block;
    font-weight: 600;
    margin-bottom: 8px;
  }

  .form-group input,
  .form-group textarea {
    width: 100%;
    box-sizing: border-box;
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 12px;
    font-size: 15px;
  }

  .form-group textarea {
    height: 220px;
    resize: vertical;
  }

  .send-button {
    width: 100%;
    background-color: #168bf2;
    color: white;
    border: none;
    border-radius: 8px;
    padding: 15px;
    font-size: 16px;
    cursor: pointer;
  }

  .send-button:hover {
    background-color: #0f76cc;
  }

  .send-button:disabled {
    background-color: #9cccf5;
    cursor: not-allowed;
  }

  .form-status {
    margin-top: 15px;
    font-size: 14px;
    color: #333;
  }

  @media screen and (max-width: 800px) {
    .contact-wrapper {
      flex-direction: column;
      gap: 30px;
    }

    .form-row {
      flex-direction: column;
      gap: 0;
    }

    .contact-left h1 {
      font-size: 34px;
    }
  }
</style>

<div class="contact-wrapper">

  <div class="contact-left">
    <div class="tag">✈ Consult Us</div>

    <h1>We’d Love to<br>Hear from You<br>and Connect</h1>

    <p>
      We welcome enquiries regarding research questions, collaboration opportunities,
      and project implementation.
    </p>
  </div>

  <div class="contact-form-box">
    <form id="contactForm">
      <div class="form-row">
        <div class="form-group">
          <label>First Name *</label>
          <input type="text" name="firstName" required>
        </div>

        <div class="form-group">
          <label>Last Name *</label>
          <input type="text" name="lastName" required>
        </div>
      </div>

      <div class="form-group">
        <label>Email *</label>
        <input type="email" name="email" required>
      </div>

      <div class="form-group">
        <label>Message *</label>
        <textarea name="message" required></textarea>
      </div>

      <button type="submit" class="send-button" id="sendButton">Send Message</button>

      <div id="formStatus" class="form-status"></div>
    </form>
  </div>

</div>

<script>
  const scriptURL = "https://script.google.com/macros/s/AKfycbyLPafx4Rslv6Di3JCmYDpi2r0gV0pW-V9U7iQeAf2Zr5XurBLxC_yHaFt_gmZgKDYi1w/exec";

  const form = document.getElementById("contactForm");
  const status = document.getElementById("formStatus");
  const sendButton = document.getElementById("sendButton");

  form.addEventListener("submit", function(event) {
    event.preventDefault();

    status.textContent = "Sending...";
    sendButton.disabled = true;

    fetch(scriptURL, {
      method: "POST",
      mode: "no-cors",
      body: new FormData(form)
    })
    .then(function() {
      status.textContent = "Message sent successfully.";
      form.reset();
      sendButton.disabled = false;
    })
    .catch(function() {
      status.textContent = "Failed to send. Please try again later.";
      sendButton.disabled = false;
    });
  });
</script>
