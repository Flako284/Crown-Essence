<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Crown Essence</title>

  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap" rel="stylesheet">

  <!-- Icons -->
  <script src="https://unpkg.com/feather-icons"></script>

  <!-- Firebase SDK -->
  <script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/10.11.0/firebase-app.js";
    import { getFirestore, collection, addDoc } from "https://www.gstatic.com/firebasejs/10.11.0/firebase-firestore.js";

    const firebaseConfig = {
      apiKey: "YOUR_API_KEY",
      authDomain: "YOUR_AUTH_DOMAIN",
      projectId: "YOUR_PROJECT_ID",
      storageBucket: "YOUR_STORAGE_BUCKET",
      messagingSenderId: "YOUR_SENDER_ID",
      appId: "YOUR_APP_ID"
    };

    const app = initializeApp(firebaseConfig);
    const db = getFirestore(app);

    window._firestore = db;
    window._addDoc = addDoc;
    window._collection = collection;
  </script>
  <script>
    document.addEventListener("DOMContentLoaded", () => {
      const form = document.getElementById("bookingForm");
      const message = document.getElementById("toast");

      if (!form || !window._firestore) return;

      form.addEventListener("submit", async (e) => {
        e.preventDefault();
        const name = form.name.value.trim();
        const style = form.hairstyle.value;
        const date = form.date.value;
        const time = form.time.value;
        const stylist = form.stylist.value;
        const notes = form.notes.value;

        try {
          await window._addDoc(window._collection(window._firestore, "appointments"), {
            name, style, date, time, stylist, notes, timestamp: new Date()
          });
          showToast("✨ Appointment Booked Successfully!");
          form.reset();
        } catch (error) {
          showToast("❌ Booking failed: " + error.message, true);
        }
      });

      function showToast(text, error = false) {
        message.textContent = text;
        message.style.backgroundColor = error ? "#e74c3c" : "#2ecc71";
        message.classList.add("show");
        setTimeout(() => message.classList.remove("show"), 3000);
      }

      const today = new Date().toISOString().split("T")[0];
      document.getElementById("date").min = today;
    });
  </script>

  <style>
    * {
      box-sizing: border-box;
    }
    body {
      font-family: 'Poppins', sans-serif;
      margin: 0;
      background: linear-gradient(to right, #0d0d0d, #1a1a1a);
      color: #f3f3f3;
    }
    header {
      background: linear-gradient(135deg, #c678dd, #8a2be2);
      color: white;
      padding: 60px 20px;
      text-align: center;
      clip-path: ellipse(75% 100% at 50% 0%);
    }
    header h1 {
      font-size: 3em;
    }
    .gallery {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 20px;
      padding: 40px 20px;
    }
    .style {
      background: #2c2c54;
      border-radius: 16px;
      overflow: hidden;
      box-shadow: 0 10px 20px rgba(0,0,0,0.5);
      transition: transform 0.3s ease;
      width: 220px;
      text-align: center;
      color: #fff;
    }
    .style:hover {
      transform: translateY(-5px);
    }
    .style img {
      width: 100%;
      height: 200px;
      object-fit: cover;
      display: block;
    }
    .style p {
      padding: 10px;
    }
    .booking-form {
      background: rgba(255,255,255,0.07);
      backdrop-filter: blur(10px);
      max-width: 600px;
      margin: 40px auto;
      padding: 30px;
      border-radius: 16px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.3);
    }
    .booking-form h2 {
      text-align: center;
      color: #dcd6f7;
      margin-bottom: 20px;
    }
    .booking-form label {
      display: block;
      margin-top: 15px;
      font-weight: 500;
    }
    .booking-form input,
    .booking-form select,
    .booking-form textarea {
      width: 100%;
      padding: 12px;
      border-radius: 8px;
      border: 1px solid #ccc;
      margin-top: 5px;
      font-size: 1em;
      background: #2f2f4f;
      color: #f3f3f3;
    }
    .booking-form button {
      margin-top: 25px;
      width: 100%;
      padding: 14px;
      background: #9b59b6;
      color: white;
      font-size: 1.1em;
      font-weight: bold;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: background 0.3s ease;
    }
    .booking-form button:hover {
      background: #732d91;
    }
    footer {
      background-color: #8e44ad;
      color: white;
      text-align: center;
      padding: 25px 15px;
      margin-top: 40px;
    }
    #toast {
      position: fixed;
      bottom: 30px;
      left: 50%;
      transform: translateX(-50%);
      background: #2ecc71;
      color: white;
      padding: 16px 24px;
      border-radius: 10px;
      font-weight: bold;
      box-shadow: 0 6px 12px rgba(0,0,0,0.2);
      opacity: 0;
      pointer-events: none;
      transition: all 0.4s ease;
      z-index: 999;
    }
    #toast.show {
      opacity: 1;
      pointer-events: auto;
      transform: translateX(-50%) translateY(-10px);
    }
  </style>
</head>
<body>

<header>
  <h1>Crown Essence</h1>
  <p>Royal Styles for Every Crown – Book Your Transformation!</p>
</header>

<section class="gallery">
  <div class="style"><img src="https://i.imgur.com/DEMO1.jpg" alt="Box Braids"/><p>Box Braids</p></div>
  <div class="style"><img src="https://i.imgur.com/DEMO2.jpg" alt="Cornrows"/><p>Cornrows</p></div>
  <div class="style"><img src="https://i.imgur.com/DEMO3.jpg" alt="Knotless Braids"/><p>Knotless Braids</p></div>
  <div class="style"><img src="https://i.imgur.com/DEMO4.jpg" alt="Senegalese Twists"/><p>Senegalese Twists</p></div>
  <div class="style"><img src="https://i.imgur.com/DEMO5.jpg" alt="Passion Twists"/><p>Passion Twists</p></div>
  <div class="style"><img src="https://i.imgur.com/DEMO6.jpg" alt="High Bun"/><p>High Bun</p></div>
  <div class="style"><img src="https://i.imgur.com/DEMO7.jpg" alt="Low Sleek Bun"/><p>Low Sleek Bun</p></div>
</section>

<section class="booking-form">
  <h2>Book an Appointment</h2>
  <form id="bookingForm">
    <label for="name">Full Name:</label>
    <input type="text" id="name" name="name" placeholder="Jane Doe" required />

    <label for="hairstyle">Choose Hairstyle:</label>
    <select id="hairstyle" name="hairstyle" required>
      <option value="">Select a style</option>
      <option value="Box Braids">Box Braids</option>
      <option value="Cornrows">Cornrows</option>
      <option value="Knotless Braids">Knotless Braids</option>
      <option value="Goddess Braids">Goddess Braids</option>
      <option value="Fulani Braids">Fulani Braids</option>
      <option value="Micro Braids">Micro Braids</option>
      <option value="Lemonade Braids">Lemonade Braids</option>
      <option value="Senegalese Twists">Senegalese Twists</option>
      <option value="Marley Twists">Marley Twists</option>
      <option value="Passion Twists">Passion Twists</option>
      <option value="Havana Twists">Havana Twists</option>
      <option value="Bantu Knots">Bantu Knots</option>
      <option value="High Bun">High Bun</option>
      <option value="Low Sleek Bun">Low Sleek Bun</option>
    </select>

    <label for="stylist">Preferred Stylist:</label>
    <select id="stylist" name="stylist">
      <option value="Any">Any Available</option>
      <option value="Stylist A">Stylist A</option>
      <option value="Stylist B">Stylist B</option>
    </select>

    <label for="date">Select Date:</label>
    <input type="date" id="date" name="date" required />

    <label for="time">Select Time:</label>
    <input type="time" id="time" name="time" required />

    <label for="notes">Additional Notes:</label>
    <textarea id="notes" name="notes" rows="3" placeholder="Special requests or info..."></textarea>

    <button type="submit">Book Now</button>
  </form>
</section>

<div id="toast"></div>

<footer>
  <p><i data-feather="phone"></i> (123) 456-7890 | <i data-feather="mail"></i> info@crownessence.com</p>
  <p><i data-feather="map-pin"></i> 123 Queen's Way, Royal City</p>
</footer>

<script>
  feather.replace();
</script>

</body>
</html>
