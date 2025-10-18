# Form Validation Interface

## 1. Project Title and Description

This project implements a functional and visually appealing form validation interface for user registration. It includes input fields for Name, Email, and Password. The application provides real-time validation feedback below each input field and disables the submission button until all fields meet the specified validation criteria. Upon successful submission, a confirmation message is displayed. The interface is styled using Bootstrap 5 for a clean, modern, and fully responsive design.

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
    *   **Password:** Enter a password. The field will show an error if it's less than 8 characters long.
3.  **Observe real-time validation:** As you type, the application will provide immediate visual feedback (green for valid, red for invalid) and display validation messages below the input fields if they are invalid.
4.  **Submit the form:** The "Register" button will remain disabled until all three fields (Name, Email, Password) meet their respective validation requirements. Once all fields are valid, the button will become enabled.
5.  **View result:** Click the "Register" button. A success message ("Success! Registration successful. Welcome.") will appear below the form in green text if the submission is valid. If there are still errors (e.g., you click submit after making an error without the input event catching it), an error message will be displayed.
6.  **Form Reset:** Upon successful submission, the form fields will clear, and the validation states will reset, disabling the submit button again.

## 4. Code Explanation

The entire application is contained within a single `index.html` file, leveraging client-side technologies:

*   **`index.html` (HTML Structure):** Defines the basic page structure, links to Bootstrap 5 CSS and JS CDNs, and contains the form elements (Name, Email, Password inputs, Submit button, and a result display area). Each input has an associated `div` with the `invalid-feedback` class to display validation messages.

*   **CSS (Inline in `index.html`):** Minimal custom CSS is used to center the form, provide a maximum width, and add a subtle box-shadow for visual appeal. It primarily relies on Bootstrap's utility and form classes for responsive styling.

*   **JavaScript (Inline in `index.html`):** This is the core logic for form validation.
    *   **DOM Element Selection:** All necessary input fields, feedback divs, the submit button, and the result area are selected using `document.querySelector`.
    *   **`validateName()`:** Checks if the name input's trimmed value is not empty.
    *   **`validateEmail()`:** Uses a regular expression (`/^[\S]+@[\S]+\.[\S]+$/`) to check for a valid email format.
    *   **`validatePassword()`:** Verifies if the password input's length is at least 8 characters.
    *   **`updateValidationState(inputElement, feedbackElement, isValid, invalidMessage)`:** A helper function that adds/removes Bootstrap's `is-valid` and `is-invalid` classes to the `inputElement`. When `is-invalid` is added, the `feedbackElement` (which has the `invalid-feedback` class) becomes visible and its text content is updated with `invalidMessage`.
    *   **`checkAllFields()`:** This function orchestrates the validation process. It calls `validateName()`, `validateEmail()`, and `validatePassword()`. Based on their return values, it enables or disables the `submitButton`.
    *   **Event Listeners:**
        *   `input` event listeners are attached to `nameInput`, `emailInput`, and `passwordInput`. These trigger `checkAllFields()` on every keypress, providing real-time validation feedback.
        *   A `submit` event listener is attached to the form. It prevents the default browser submission, re-runs `checkAllFields()` for a final check, and then displays a success or error message in the `#form-result` div. Upon success, the form is reset, and validation classes are cleared.
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
