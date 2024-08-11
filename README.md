# age-verification


{% if template.name == 'index' %}
  <!-- Age Verification Popup -->
  <div id="age-verification-popup" class="age-verification-popup">
    <div class="age-verification-content">
      <img src="{{ 'your_logo.png' | asset_url }}" alt="Logo" class="age-verification-logo">

      <h2>Are you over 21 years of age?</h2>
      <p>Verify your age to continue</p>
      <div class="age-verification-buttons">
        <button id="age-yes" class="age-yes">Agree</button>
        <button id="age-no" class="age-no">Disagree</button>
      </div>
    </div>
  </div>

  <style>
    .age-verification-popup {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 0, 20,0.9);
      display: flex;
      justify-content: center;
      align-items: center;
      z-index: 9999;
    }

    .age-verification-content {
      background: white;
      padding: 20px;
      text-align: center;
      border-radius: 10px;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    }
    .age-verification-content h2{
      font-size:2rem;
      font-weight: bold;
    }

    .age-verification-logo {
      width: 100px;
      margin-bottom: 20px;
    }

    .age-verification-buttons{
      display: flex;
      justify-content: center;
      align-items: center;
      
    }

    .age-verification-buttons button {
      padding: 10px 20px;
      margin: 10px;
      border: none;
      border-radius: 5px;
      cursor: pointer;
      font-size: 16px;
    }

    .age-yes {
      background-color: #28a745;
      color: white;
    }

    .age-no {
      background-color: #dc3545;
      color: white;
    }
  </style>

  <script>
    document.addEventListener('DOMContentLoaded', function() {
      var agePopup = document.getElementById('age-verification-popup');
      var ageYes = document.getElementById('age-yes');
      var ageNo = document.getElementById('age-no');

      ageYes.addEventListener('click', function() {
        localStorage.setItem('ageVerified', 'true');
        agePopup.style.display = 'none';
      });

      ageNo.addEventListener('click', function() {
        window.location.href = 'https://www.google.com'; // Redirect if under 21
      });

      if (!localStorage.getItem('ageVerified')) {
        agePopup.style.display = 'flex';
      } else {
        agePopup.style.display = 'none';
      }
    });
  </script>
{% endif %}
