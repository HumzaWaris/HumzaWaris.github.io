<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Epic Math Helper</title>
    <script>
        // Function to calculate GCD
        function gcd(a, b) {
            if (b === 0) {
                return a;
            }
            return gcd(b, a % b);
        }

        // Function to check if a number is prime
        function isPrime(n) {
            if (n < 2) return false;
            for (let i = 2; i <= Math.sqrt(n); i++) {
                if (n % i === 0) {
                    return false;
                }
            }
            return true;
        }

        // Function to perform prime factorization
        function primeFactorization(n) {
            let factors = [];
            while (n % 2 === 0) {
                factors.push(2);
                n /= 2;
            }
            for (let i = 3; i <= Math.sqrt(n); i += 2) {
                while (n % i === 0) {
                    factors.push(i);
                    n /= i;
                }
            }
            if (n > 2) {
                factors.push(n);
            }
            return factors;
        }

        // Function to handle button click and display results
        function calculate() {
            const operation = parseInt(document.getElementById('operation').value);
            const n1 = parseInt(document.getElementById('num1').value);
            const n2 = parseInt(document.getElementById('num3').value);

            let result = '';
            if (operation === 1) {
                // GCD Calculation
                if (!isNaN(n1) && !isNaN(n2) && n1 > 0 && n2 > 0) {
                    result = 'GCD: ' + gcd(n1, n2);
                } else {
                    result = 'Invalid input for GCD!';
                }
            } else if (operation === 2) {
                // Prime Factorization
                if (!isNaN(n1) && n1 >= 2) {
                    result = 'Prime Factors: ' + primeFactorization(n1).join(' x ');
                } else {
                    result = 'Invalid input for Prime Factorization!';
                }
            } else if (operation === 3) {
                result = 'Thank you for using My Math Helper!';
            } else {
                result = 'Invalid menu selection!';
            }

            // Display the result
            document.getElementById('result').innerText = result;
        }
    </script>
</head>
<body>
    <h1>Welcome to My Math Helper!</h1>

    <h2>Please Select an Operation:</h2>
    <select id="operation">
        <option value="1">1 - Calculate Greatest Common Denominator (GCD)</option>
        <option value="2">2 - Perform Prime Factorization</option>
        <option value="3">3 - Exit</option>
    </select>

    <p>Please Enter an Integer:</p>
    <input type="number" id="num1" placeholder="Enter first number">

    <p id="num2Input" style="display: none;">Please Enter a Second Integer:</p>
    <input type="number" id="num2" placeholder="Enter second number" style="display: none;">
    <input type="number" id="num3" placeholder="Enter the actual second number lol" style="display: none;">

    <br><br>
    <button onclick="calculate()">Submit</button>

    <h3 id="result"></h3>

    <script>
        // Show/hide second input field based on the selected operation
        document.getElementById('operation').addEventListener('change', function () {
            const selectedOperation = parseInt(this.value);
            if (selectedOperation === 1) {
                document.getElementById('num3Input').style.display = 'block';
                document.getElementById('num3').style.display = 'block';
            } else {
                document.getElementById('num3Input').style.display = 'none';
                document.getElementById('num3').style.display = 'none';
            }
        });
    </script>
</body>
</html>

