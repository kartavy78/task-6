# task-6

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Contact Form</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 20px;
    }
    form {
      max-width: 400px;
      margin: auto;
    }
    label {
      display: block;
      margin-top: 10px;
    }
    input, textarea {
      width: 100%;
      padding: 8px;
      margin-top: 5px;
    }
    .error {
      color: red;
      font-size: 0.9em;
    }
    button {
      margin-top: 15px;
      padding: 10px 15px;
    }
  </style>
</head>
<body>

  <h2>Contact Us</h2>
  <form id="contactForm">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name">
    <div id="nameError" class="error"></div>

    <label for="email">Email:</label>
    <input type="text" id="email" name="email">
    <div id="emailError" class="error"></div>

    <label for="message">Message:</label>
    <textarea id="message" name="message" rows="5"></textarea>
    <div id="messageError" class="error"></div>

    <button type="submit">Submit</button>
  </form>

  <script>
    const form = document.getElementById('contactForm');

    form.addEventListener('submit', function (e) {
      e.preventDefault();

      // Clear previous errors
      document.getElementById('nameError').textContent = '';
      document.getElementById('emailError').textContent = '';
      document.getElementById('messageError').textContent = '';

      // Get form values
      const name = document.getElementById('name').value.trim();
      const email = document.getElementById('email').value.trim();
      const message = document.getElementById('message').value.trim();

      let isValid = true;

      // Name validation
      if (name.length < 3) {
        document.getElementById('nameError').textContent = 'Name must be at least 3 characters.';
        isValid = false;
      }

      // Email validation (basic regex)
      const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      if (!emailPattern.test(email)) {
        document.getElementById('emailError').textContent = 'Enter a valid email address.';
        isValid = false;
      }

      // Message validation
      if (message.length < 10) {
        document.getElementById('messageError').textContent = 'Message must be at least 10 characters.';
        isValid = false;
      }

      if (isValid) {
        alert('Form submitted successfully!');
        form.reset();
      }
    });
  </script>

</body>
</html>
