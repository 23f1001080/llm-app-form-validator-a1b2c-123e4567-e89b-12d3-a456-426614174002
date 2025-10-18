# Form Validation Interface

## 1. Project Title and Description

This project implements a functional and visually appealing user registration form. It enhances the previous version with advanced password validation rules, including a 'Confirm Password' field that must exactly match the primary password. Crucially, it demonstrates asynchronous form submission using the native JavaScript `fetch` API, sending validated user data (Name, Email, Password) as JSON to a specified endpoint with appropriate headers. The application provides real-time validation feedback, disables the submission button until all criteria are met, and displays submission progress and results dynamically.

## 2. Setup Instructions

This application is a single-page HTML file with embedded CSS and JavaScript, making it incredibly easy to set up and run.

1.  **Clone the repository (or copy the `index.html` file):**

    If this were a repository, you would clone it using:
    ```bash
    git clone <repository-url>
    cd <repository-directory>
    ```
    Since the code is provided directly, simply save the content of `index.html` into a file named `index.html` on your local machine.

2.  **Open in your browser:**

    Navigate to the directory where you saved `index.html` and open the file directly with your web browser (e.g., by double-clicking it). No server-side setup or build process is required.

## 3. Usage Guide

Follow these steps to use the form validation interface:

1.  **Open the application:** Launch the `index.html` file in your web browser.
2.  **Fill in the fields:**
    *   **Name:** Enter your name. The field will show an error if left empty.
    *   **Email:** Enter a valid email address (e.g., `user@example.com`). The field will show an error if the format is incorrect.
    *   **Password:** Enter a password. This field now requires at least 8 characters, including at least one digit, one lowercase letter, one uppercase letter, and one special character (`!@#$%^&*`). The field will show an error if these criteria are not met.
    *   **Confirm Password:** Re-enter the exact same password as entered in the 'Password' field. This field will show an error if it does not match the 'Password' field or is left empty.
3.  **Observe real-time validation:** As you type, the application will provide immediate visual feedback (green for valid, red for invalid) and display validation messages below the input fields if they are invalid.
4.  **Submit the form:** The "Register" button will remain disabled until all four fields (Name, Email, Password, Confirm Password) meet their respective validation requirements. Once all fields are valid, the button will become enabled.
5.  **View result:** Click the "Register" button.
    *   The form will display "Submission in progress..." below the form while the data is being sent to the server.
    *   If the submission is successful (the server responds with a 2xx status code), "Submission successful!" will be displayed in green, and the form fields will clear and reset.
    *   If there's a network error or the server responds with an error status, an appropriate error message will be shown in red.

## 4. Code Explanation

The entire application is contained within a single `index.html` file, leveraging client-side technologies:

*   **`index.html` (HTML Structure):** Defines the basic page structure, links to Bootstrap 5 CSS and JS CDNs, and contains the form elements (Name, Email, Password, Confirm Password inputs, Submit button, and a result display area). Each input has an associated `div` with the `invalid-feedback` class to display validation messages.

*   **CSS (Inline in `index.html`):** Minimal custom CSS is used for layout and visual styling. It primarily relies on Bootstrap's utility and form classes for responsive design.

*   **JavaScript (Inline in `index.html`):** This is the core logic for form validation and submission.
    *   **DOM Element Selection:** All necessary input fields (including the new `confirmPasswordInput`), feedback divs, the submit button, and the result area are selected using `document.querySelector`.
    *   **`evaluation_url`:** A constant `evaluation_url` (set to `https://jsonplaceholder.typicode.com/posts` for demonstration purposes) defines the target endpoint for the form data submission.
    *   **`validateName()`:** Checks if the name input's trimmed value is not empty.
    *   **`validateEmail()`:** Uses a regular expression (`/^\S+@\S+\.\S+$/`) to check for a valid email format.
    *   **`validatePassword()`:** Updated with a robust regular expression (`/^(?=.*[a-z])(?=.*[A-Z])(?=.*[0-9])(?=.*[!@#$%^&*]).{8,}$/`) to enforce the new complexity requirements: at least 8 characters long, containing at least one digit, one lowercase letter, one uppercase letter, and one special character.
    *   **`validateConfirmPassword()`:** A new function that checks if the 'Confirm Password' field is not empty and exactly matches the 'Password' field.
    *   **`updateValidationState(inputElement, feedbackElement, isValid, invalidMessage)`:** A helper function that adds/removes Bootstrap's `is-valid` and `is-invalid` classes, and updates the text content of the feedback element.
    *   **`checkAllFields()`:** This function orchestrates the validation process for all fields, including the new `confirmPasswordInput`. It enables or disables the `submitButton` based on the overall validity.
    *   **Event Listeners:**
        *   `input` event listeners are attached to `nameInput`, `emailInput`, `passwordInput`, and `confirmPasswordInput`. These trigger `checkAllFields()` on every keypress, providing real-time validation feedback.
        *   A `submit` event listener is attached to the form. It's now an `async` function. After preventing default submission and re-validating all fields, it displays "Submission in progress...", disables the submit button, and uses the `fetch` API to POST the form data (Name, Email, Password) as a JSON object to the `evaluation_url`. Proper headers (`Content-Type: application/json`, `Accept: application/json`) are included. It then handles the server response: displaying "Submission successful!" on a 2xx status, or an error message otherwise. The form is reset on successful submission, and the submit button is re-enabled in case of submission failure.
    *   **`DOMContentLoaded`:** Ensures the JavaScript runs only after the entire HTML document has been loaded and parsed.

## 5. License Information

This project is licensed under the MIT License.

```
MIT License

Copyright (c) [Year] [Your Name/Organization]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
