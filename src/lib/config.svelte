<script context='module' >

  import { initializeApp } from "https://www.gstatic.com/firebasejs/9.6.10/firebase-app.js";
  import { getFirestore } from "https://www.gstatic.com/firebasejs/9.6.10/firebase-firestore.js";

  const firebaseConfig = {
    apiKey: "AIzaSyBVk5ZkbyeJUjiRyj_WCGSY3tXA96sRblc",
    authDomain: "whatsapp-v2-ddd9f.firebaseapp.com",
    projectId: "whatsapp-v2-ddd9f",
    storageBucket: "whatsapp-v2-ddd9f.appspot.com",
    messagingSenderId: "667004500109",
    appId: "1:667004500109:web:8a56b66b9061ef513d8ac4",
    measurementId: "G-4QBHJGTH0T"
  };

  // Initialize Firebase
  export const app = initializeApp(firebaseConfig);
  export const db = getFirestore(app)
</script>