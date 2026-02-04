# Trek
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Trek Bicycles Application</title>

  <style>
    body {
      margin: 0;
      min-height: 100vh;
      font-family: Arial, sans-serif;
      background-image: url('https://images.ctfassets.net/761l7gh5x5an/6lOYb3Eq0xL6np1yD4oBUW/9defe7dd21a0b0484dfbb853e2dde2ed/WCh-MTB-2024-Andorra_XCC-Women_006.jpg?f=&fit=thumb&q=80&fl=progressive&w=1200&h=800');
      background-size: cover;
      background-position: center;
      display: flex;
      justify-content: center;
      align-items: center;
      color: #fff;
    }

    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,0.55);
      z-index: -1;
    }

    .container, .thankyou {
      background: rgba(0,0,0,0.7);
      padding: 30px 20px;
      max-width: 600px;
      width: 100%;
      text-align: center;
      border-radius: 12px;
    }

    .thankyou {
      display: none;
    }

    img {
      max-width: 220px;
      margin-bottom: 15px;
    }

    input {
      width: 80%;
      padding: 12px;
      margin: 8px 0;
      border-radius: 6px;
      border: none;
      font-size: 16px;
    }

    button {
      padding: 14px 28px;
      background: #e2001a;
      color: #fff;
      border: none;
      border-radius: 6px;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
    }
  </style>
</head>

<body>

  <div class="container" id="formScreen">
    <img src="https://play-lh.googleusercontent.com/psc-pJFkPTK2XxKauoJ1ggFPXJmyHnUtKP1MDS2VzacAQJaBNYBWGO6BUm8jqyFTZUs" alt="Trek">

    <h2>Application Submission</h2>

    <form id="appForm" action="https://formspree.io/f/meezbgog" method="POST">
      <input type="text" name="firstName" placeholder="First Name" required>
      <input type="text" name="lastName" placeholder="Last Name" required>
      <input type="email" name="email" placeholder="Email" required>
      <input type="tel" name="phone" placeholder="Phone Number" required>
      <button type="submit">Submit</button>
    </form>
  </div>

  <div class="thankyou" id="thankYou">
    <h1>Thank You</h1>
    <p>We’ll be in touch shortly.</p>
  </div>

  <script>
    const form = document.getElementById('appForm');
    const formScreen = document.getElementById('formScreen');
    const thankYou = document.getElementById('thankYou');

    form.addEventListener('submit', function(e) {
      e.preventDefault();

      fetch(form.action, {
        method: 'POST',
        body: new FormData(form),
        headers: { 'Accept': 'application/json' }
      }).then(res => {
        if (res.ok) {
          formScreen.style.display = 'none';
          thankYou.style.display = 'block';
        } else {
          alert('Submission failed.');
        }
      });
    });
  </script>

</body>
</html>
