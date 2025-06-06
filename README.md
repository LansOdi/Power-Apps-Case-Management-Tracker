# Case Document Management Tracker - Power Apps

A Power Apps Canvas App for managing legal case documents. This project was built as a portfolio piece to demonstrate skills in low-code app development, data modeling, and UI/UX design within the Microsoft Power Platform.

---

## 🚀 Project Demo

Click the thumbnail below to watch a one-minute video demonstration of the app in action, showcasing case creation and the document upload process.

[![Power Apps Case Management Demo](video-thumbnail.png)](https://vimeo.com/1091309000?share=copy)

---

## ✨ Features

* **Case Management:** View a list of all cases from a Dataverse backend.
* **Document Metadata Entry:** A user-friendly form to input document details like Document Name, Category (Choice), and Status (Choice).
* **Robust File Upload:** Attach various file types (PDF, DOCX, PNG, etc.) directly to a case record using an integrated attachments control.
* **Dataverse File Storage:** The file is stored securely within the Dataverse "Case Document" table alongside its metadata, ensuring data integrity.
* **Dynamic Case Linking:** The document upload form automatically links the new document to the case selected on the main screen.
* **Responsive Feedback:** The app provides clear success and error notifications to the user upon submission using form-based event handling (`OnSuccess`, `OnFailure`).

---

## 🛠️ Tech Stack & Architecture

This solution utilizes key components of the Microsoft Power Platform to create an integrated system:

* **Microsoft Power Apps:** The user interface was built using Canvas Apps.
* **Microsoft Dataverse:** Used as the primary backend for storing structured case data, document metadata, and for native file storage.
* **Microsoft Power Automate:** A cloud flow was developed to demonstrate an alternative architecture for handling file uploads by routing documents to a separate cloud storage location like OneDrive. (This flow is included in the solution but is not wired up to the final version of the app's upload button).

---

## 📸 Screenshots

| Cases Screen | Upload Screen with File |
| :---: | :---: |
| ![Cases Screen](screenshots/Cases_Screen.JPG) | ![Upload Screen](screenshots/Upload_Screen_Empty.JPG) |

---

## 🧠 Challenges & Solutions

This project involved several key design decisions and debugging challenges that demonstrate a deep understanding of the Power Platform.

* **Challenge 1: Designing the File Handling Architecture.** I evaluated two primary methods for handling file uploads:
    1.  **Power Automate Flow:** An initial flow was built to route files to a OneDrive storage location. This demonstrates skill in process automation and integrating multiple services.
    2.  **Native Dataverse File Column:** A second approach using Dataverse's built-in "File" data type.
    * **Solution:** For the final, functional version of the app, I chose to implement the **Dataverse File Column** method. This approach simplifies the Power Apps formula logic, enhances data integrity by keeping the file and its metadata in the same record, and improves reliability by using native form controls. The Power Automate flow remains in the solution as a demonstration of alternative architectural skills.

* **Challenge 2: Debugging Dataverse Lookup Fields.** The "Case (Lookup)" field initially produced a "Value must be a data entity record" error.
    * **Solution:** I resolved this by meticulously debugging the form control properties. The fix required setting the `Items` property of the lookup's ComboBox to the parent table (`Cases`) and setting the `DefaultSelectedItems` property to `RecordsGallery1.Selected`. This ensures the full record object, not just an ID, is passed to the form, satisfying Dataverse's data integrity requirements. This process demonstrates advanced debugging and a nuanced understanding of Power Fx formulas.
