<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>New Lead</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 30px;
    }
    form {
      max-width: 400px;
    }
    label {
      font-weight: bold;
      margin-top: 10px;
    }
    input, textarea, button {
      width: 100%;
      padding: 10px;
      margin-top: 5px;
      margin-bottom: 15px;
      border: 1px solid #ddd;
      border-radius: 5px;
    }
    button {
      background-color: #007bff;
      color: white;
      border: none;
      cursor: pointer;
    }
    button:hover {
      background-color: #0056b3;
    }
  </style>
</head>
<body>
  <h1>Add a New Sales Lead</h1>
  <form id="leadForm">
    <label for="company">Company Name</label>
    <input type="text" id="company" name="company" placeholder="Acme Corp" required>

    <label for="contact">Contact Person</label>
    <input type="text" id="contact" name="contact" placeholder="John Doe" required>

    <label for="email">Email</label>
    <input type="email" id="email" name="email" placeholder="example@domain.com">

    <label for="notes">Notes</label>
    <textarea id="notes" name="notes" placeholder="Any relevant information about the lead..."></textarea>

    <button type="submit">Add Lead</button>
  </form>

  <script>
    document.getElementById('leadForm').addEventListener('submit', async (event) => {
      event.preventDefault();

      const leadData = {
        company: document.getElementById('company').value,
        contact: document.getElementById('contact').value,
        email: document.getElementById('email').value,
        notes: document.getElementById('notes').value,
      };

      const response = await fetch('/api/leads', {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(leadData),
      });

      if (response.ok) {
        alert('Lead added successfully!');
        document.getElementById('leadForm').reset();
      } else {
        alert('Failed to add lead. Please try again.');
      }
    });
  </script>
</body>
</html># Nilay
