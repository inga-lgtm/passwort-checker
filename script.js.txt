document.getElementById("togglePassword").addEventListener("click", function () {
  const passwordInput = document.getElementById("password");
  const type = passwordInput.getAttribute("type") === "password" ? "text" : "password";
  passwordInput.setAttribute("type", type);
});

function verifizieren() {
  const password = document.getElementById("password").value;
  const resultat = document.getElementById("resultat");
  const bar = document.getElementById("bar");

  let stärke = 0;

  if (password.length >= 6) stärke++;
  if (/[A-Z]/.test(password)) stärke++;
  if (/[0-9]/.test(password)) stärke++;
  if (/[@$!%*?&]/.test(password)) stärke++;

  let farbe = "red";
  let breite = "25%";
  let text = "Sehr schwach";

  switch (stärke) {
    case 1:
      text = "Sehr schwach";
      farbe = "red";
      breite = "25%";
      break;
    case 2:
      text = "Schwach";
      farbe = "orange";
      breite = "50%";
      break;
    case 3:
      text = "Starkes Passwort";
      farbe = "green";
      breite = "100%";
      break;
  }

  resultat.textContent = text;
  resultat.style.color = farbe;
  bar.style.setProperty("--bar", breite);
  bar.innerHTML = `<div style="width: ${breite}; background: ${farbe}; height: 100%"></div>`;
}
