# dawnwash-live
# DawnWash - Car Cleaning Service (Web Demo)

A simple, single-page web application demo for managing car cleaning service schedules and status updates. It features separate views for an administrator and customers, using Firebase Firestore for data storage.

## Features

* **Admin Login:** Secure login using a hardcoded username (`admin`) and password.
* **Customer Login:** Login using just a registered phone number.
* **Car Registration:** Both admin and customers can register new cars with:
    * Customer Phone Number (acts as User ID)
    * Car Number
    * Service Start Date
    * Weekly Cleaning Schedule (External Cleaning 'EC' / Full Cleaning 'FC' / None for Mon-Sat)
* **Admin Dashboard:**
    * View a list of all registered customer cars.
    * Search cars by phone number or car number.
    * Update the cleaning status (Pending/Completed) for each scheduled day via toggles.
    * View the 4-week service period (Start Date to End Date).
    * Update the payment status (Pending/Received) for the current service period via a toggle.
    * Add new customer cars.
* **Customer Dashboard:**
    * View all cars registered under their phone number.
    * See the current cleaning status for each scheduled day for each car.
    * View the current 4-week service period.
    * View the payment status for the current service period.
* **Static Pages:** Includes basic "About Us" and "Contact Us" sections.
* **Data Persistence:** Uses Google Firebase Firestore to store all car, schedule, status, and payment data permanently.
* **Responsive Design:** Basic responsiveness for viewing on different screen sizes.

## Tech Stack

* **Frontend:** HTML, CSS, JavaScript (all within `index.html`)
* **Database:** Google Firebase Firestore (Cloud-based NoSQL database)

## Setup and Configuration

To run or modify this project, you need to configure Firebase:

1.  **Create a Firebase Project:**
    * Go to the [Firebase Console](https://console.firebase.google.com/).
    * Create a new project (e.g., `dawnwash-data`).
    * Disable Google Analytics if not needed.

2.  **Set up Firestore Database:**
    * In your Firebase project, navigate to **Firestore Database** (under Build).
    * Click **Create database**.
    * Start in **test mode** (Remember to secure rules later!).
    * Choose a Firestore location (e.g., `asia-south1`).
    * Click **Enable**.

3.  **Get Firebase Web Configuration:**
    * Go to Project Overview in your Firebase Console.
    * Click the Web icon (`</>`) to add a web app.
    * Register the app (give it a nickname, e.g., `DawnWash Web`). **Hosting is NOT needed here**.
    * Copy the `firebaseConfig` object provided.

4.  **Configure `index.html`:**
    * Open the `index.html` file in a text editor.
    * Scroll down to the main `<script>` tag near the bottom.
    * Find the `const firebaseConfig = { ... };` section.
    * **Replace the placeholder values** (`YOUR_API_KEY`, `YOUR_PROJECT_ID`, etc.) with the actual configuration values you copied from Firebase.
    * Save the file.

## Running Locally

1.  Ensure you have completed the Firebase configuration step above.
2.  Simply open the `index.html` file in your web browser.

## Deployment

This project is designed for static hosting platforms that support deploying directly from Git.

1.  Push the `index.html` file (with your Firebase config included) and this `README.md` file to a GitHub repository.
2.  Connect the GitHub repository to a service like [Netlify](https://www.netlify.com/) or [Vercel](https://vercel.com/).
3.  Configure the deployment settings (usually requires no build command and the root directory as the publish directory).
4.  Deploy the site.

## Important Considerations & Limitations

* **Security Rules:** The initial Firestore setup uses "test mode" rules which expire after 30 days and allow anyone to read/write data. **You MUST update these rules** in the Firebase console (Firestore Database -> Rules) before the expiry for the app to keep working and to secure your data. Basic permanent rules are provided in the Firebase setup instructions, but implementing Firebase Authentication is recommended for real-world security.
* **Admin Credentials:** The admin username (`admin`) and password (`sandesh043`) are hardcoded directly in the JavaScript within `index.html`. This is **highly insecure** and suitable only for a personal demo. Do not use this method for sensitive applications.
* **No User Authentication:** Customer login relies solely on entering a phone number present in the database. There is no password or verification process.
* **Single File Structure:** All HTML, CSS, and JavaScript are contained within `index.html`. While simple for a demo, this is not scalable for larger projects.
* **Firebase Dependency:** The application relies entirely on Firebase Firestore for data storage and retrieval. It will not function without a correctly configured Firebase project.
