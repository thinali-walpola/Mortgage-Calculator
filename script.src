// Get elements from HTML
const amountEl = document.getElementById("amount");
const yearsEl  = document.getElementById("years");
const rateEl   = document.getElementById("rate");
const btn      = document.getElementById("calculateBtn");

const amountError = document.getElementById("amountError");
const yearsError  = document.getElementById("yearsError");
const rateError   = document.getElementById("rateError");
const typeError   = document.getElementById("typeError");

const resultBox = document.getElementById("results");
const monthlyEl = document.getElementById("monthly");
const totalEl   = document.getElementById("total");

// When button is clicked
btn.addEventListener("click", function () {

  // Clear previous errors
  amountError.textContent = "";
  yearsError.textContent  = "";
  rateError.textContent   = "";
  typeError.textContent   = "";

  // Read values
  const amount = parseFloat(amountEl.value);
  const years  = parseFloat(yearsEl.value);
  const rate   = parseFloat(rateEl.value);

  // Get selected type
  const type = document.querySelector('input[name="type"]:checked');

  let hasError = false;

  // Validation
  if (!amount) {
    amountError.textContent = "This field is required";
    hasError = true;
  }

  if (!years) {
    yearsError.textContent = "This field is required";
    hasError = true;
  }

  if (!rate) {
    rateError.textContent = "This field is required";
    hasError = true;
  }

  if (!type) {
    typeError.textContent = "This field is required";
    hasError = true;
  }

  if (hasError) return;

  // Convert to monthly values
  const monthlyRate = (rate / 100) / 12;
  const months = years * 12;

  let monthlyPayment;
  let totalPayment;

  if (type.value === "repayment") {
    // Repayment formula
    monthlyPayment = amount * (monthlyRate * Math.pow(1 + monthlyRate, months)) 
                    / (Math.pow(1 + monthlyRate, months) - 1);

    totalPayment = monthlyPayment * months;

  } else {
    // Interest only
    monthlyPayment = amount * monthlyRate;
    totalPayment = (monthlyPayment * months) + amount;
  }

  // Show results
  resultBox.classList.remove("hidden");

  // Add £ sign and format numbers
  monthlyEl.textContent = "£" + monthlyPayment.toFixed(2);
  totalEl.textContent   = "£" + totalPayment.toFixed(2);
});
