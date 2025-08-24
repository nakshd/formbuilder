# formbuilder
<html lang="en">
 <head>
  <meta charset="utf-8" />
  <meta content="width=device-width, initial-scale=1" name="viewport" />
  <title> MERN Form Builder with Tailwind CSS </title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css"
    rel="stylesheet"
  />
  <link
    href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap"
    rel="stylesheet"
  />
  <style>
   body {
    font-family: "Inter", sans-serif;
   }
  </style>
 </head>
 <body class="bg-gray-100 min-h-screen flex flex-col">
  <header class="bg-white shadow-md">
   <div
     class="max-w-7xl mx-auto px-6 sm:px-8 lg:px-10 flex items-center justify-between h-16"
   >
    <div class="flex items-center space-x-3">
     <img
       alt="Form Builder logo icon with stylized FB letters in blue on white background"
       class="h-10 w-10 rounded"
       height="80"
       src="https://storage.googleapis.com/a1aa/image/927ea32e-b3a1-4996-95e5-e11744e7f096.jpg"
       width="80"
     />
     <h1 class="text-2xl font-semibold text-gray-900 tracking-tight">
      Form Builder Pro
     </h1>
    </div>
    <nav class="hidden md:flex space-x-8 text-gray-700 font-semibold tracking-wide">
     <a
       class="hover:text-blue-600 transition duration-200 ease-in-out"
       href="#editor"
       >Form Editor</a
     >
     <a
       class="hover:text-blue-600 transition duration-200 ease-in-out"
       href="#preview"
       >Form Preview</a
     >
     <a
       class="hover:text-blue-600 transition duration-200 ease-in-out"
       href="#submissions"
       >Submissions</a
     >
    </nav>
    <button
      aria-label="Open menu"
      class="md:hidden text-gray-700 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-blue-600"
      id="mobile-menu-button"
    >
     <i class="fas fa-bars fa-lg"></i>
    </button>
   </div>
   <nav
     aria-label="Mobile menu"
     class="md:hidden bg-white border-t border-gray-200 hidden"
     id="mobile-menu"
   >
    <a
      class="block px-6 py-3 text-gray-700 hover:bg-gray-100 font-semibold tracking-wide"
      href="#editor"
      >Form Editor</a
    >
    <a
      class="block px-6 py-3 text-gray-700 hover:bg-gray-100 font-semibold tracking-wide"
      href="#preview"
      >Form Preview</a
    >
    <a
      class="block px-6 py-3 text-gray-700 hover:bg-gray-100 font-semibold tracking-wide"
      href="#submissions"
      >Submissions</a
    >
   </nav>
  </header>
  <main class="flex-grow max-w-7xl mx-auto px-6 sm:px-8 lg:px-10 py-10">
   <!-- Form Editor Section -->
   <section class="mb-20" id="editor">
    <h2
      class="text-4xl font-extrabold text-gray-900 mb-8 tracking-tight border-b border-gray-300 pb-3"
    >
     Form Editor
    </h2>
    <div class="flex flex-col md:flex-row md:space-x-10">
     <!-- Questions List -->
     <div
       class="md:w-1/2 bg-white rounded-xl shadow-lg p-8 mb-10 md:mb-0 max-h-[650px] overflow-y-auto"
     >
      <h3 class="text-2xl font-semibold mb-6 text-gray-800 tracking-wide">
       Questions
      </h3>
      <ul class="space-y-5" id="questions-list"></ul>
      <button
        class="mt-8 w-full bg-blue-700 hover:bg-blue-800 text-white font-semibold py-3 rounded-lg shadow-md transition duration-300 flex items-center justify-center space-x-3 focus:outline-none focus:ring-4 focus:ring-blue-500"
        id="add-question-btn"
        type="button"
      >
       <i class="fas fa-plus fa-lg"></i>
       <span>Add Question</span>
      </button>
     </div>
     <!-- Question Editor -->
     <div
       class="md:w-1/2 bg-white rounded-xl shadow-lg p-8 max-h-[650px] overflow-y-auto"
     >
      <h3
        class="text-2xl font-semibold mb-6 text-gray-800 tracking-wide"
        id="question-editor-title"
      >
       Add New Question
      </h3>
      <form class="space-y-7" id="question-form" novalidate="">
       <div>
        <label
          class="block text-gray-700 font-semibold mb-2 tracking-wide"
          for="question-text"
        >
         Question Text
         <span class="text-red-600">*</span>
        </label>
        <input
          autocomplete="off"
          class="w-full border border-gray-300 rounded-lg px-4 py-3 focus:outline-none focus:ring-4 focus:ring-blue-400 transition duration-200"
          id="question-text"
          name="questionText"
          placeholder="Enter your question here"
          required=""
          type="text"
        />
       </div>
       <div>
        <label
          class="block text-gray-700 font-semibold mb-2 tracking-wide"
          for="question-type"
        >
         Question Type
         <span class="text-red-600">*</span>
        </label>
        <select
          class="w-full border border-gray-300 rounded-lg px-4 py-3 focus:outline-none focus:ring-4 focus:ring-blue-400 transition duration-200"
          id="question-type"
          name="questionType"
          required=""
        >
         <option value="text">Text Input</option>
         <option value="textarea">Textarea</option>
         <option value="radio">Multiple Choice (Single Select)</option>
         <option value="checkbox">Multiple Choice (Multi Select)</option>
         <option value="select">Dropdown Select</option>
         <option value="image">Image Upload</option>
        </select>
       </div>
       <div class="space-y-4 hidden" id="options-container">
        <label
          class="block text-gray-700 font-semibold mb-2 tracking-wide"
          >Options</label
        >
        <ul
          class="space-y-3 max-h-44 overflow-y-auto border border-gray-300 rounded-lg p-3"
          id="options-list"
        ></ul>
        <button
          class="inline-flex items-center px-4 py-2 bg-green-600 hover:bg-green-700 text-white rounded-lg text-sm font-semibold transition duration-300 focus:outline-none focus:ring-4 focus:ring-green-400"
          id="add-option-btn"
          type="button"
        >
         <i class="fas fa-plus mr-2"></i> Add Option
        </button>
       </div>
       <div class="hidden" id="image-upload-container">
        <label
          class="block text-gray-700 font-semibold mb-2 tracking-wide"
          for="image-upload"
        >
         Upload Image
        </label>
        <input
          accept="image/*"
          class="w-full rounded-lg border border-gray-300 px-3 py-2 focus:outline-none focus:ring-4 focus:ring-blue-400 transition duration-200"
          id="image-upload"
          name="imageUpload"
          type="file"
        />
        <div class="mt-4" id="image-preview"></div>
       </div>
       <div class="flex space-x-5">
        <button
          class="bg-blue-700 hover:bg-blue-800 text-white font-semibold py-3 px-6 rounded-lg shadow-md transition duration-300 focus:outline-none focus:ring-4 focus:ring-blue-500"
          type="submit"
        >
         Save Question
        </button>
        <button
          class="bg-gray-300 hover:bg-gray-400 text-gray-900 font-semibold py-3 px-6 rounded-lg shadow-md transition duration-300 focus:outline-none focus:ring-4 focus:ring-gray-400 hidden"
          id="cancel-edit-btn"
          type="button"
        >
         Cancel
        </button>
       </div>
      </form>
     </div>
    </div>
    <div class="mt-12 flex justify-end">
     <button
       class="bg-indigo-700 hover:bg-indigo-800 text-white font-semibold py-4 px-8 rounded-xl shadow-lg transition duration-300 flex items-center space-x-3 focus:outline-none focus:ring-4 focus:ring-indigo-500"
       id="save-form-btn"
       type="button"
     >
      <i class="fas fa-save fa-lg mr-3"></i>
      <span>Save Form</span>
     </button>
    </div>
   </section>
   <!-- Form Preview / Fill Section -->
   <section class="mb-20" id="preview">
    <h2
      class="text-4xl font-extrabold text-gray-900 mb-8 tracking-tight border-b border-gray-300 pb-3"
    >
     Form Preview / Fill
    </h2>
    <div
      class="bg-white rounded-xl shadow-lg p-10 max-w-4xl mx-auto border border-gray-200"
    >
     <form class="space-y-8" id="form-preview" novalidate=""></form>
     <div class="mt-10 flex justify-end">
      <button
        class="bg-green-700 hover:bg-green-800 text-white font-semibold py-4 px-8 rounded-xl shadow-lg transition duration-300 flex items-center space-x-3 focus:outline-none focus:ring-4 focus:ring-green-500"
        id="submit-answers-btn"
        type="button"
      >
       <i class="fas fa-paper-plane fa-lg mr-3"></i>
       <span>Submit Answers</span>
      </button>
     </div>
    </div>
   </section>
   <!-- Submissions Section -->
   <section class="mb-20" id="submissions">
    <h2
      class="text-4xl font-extrabold text-gray-900 mb-8 tracking-tight border-b border-gray-300 pb-3"
    >
     Submissions
    </h2>
    <div
      class="bg-white rounded-xl shadow-lg p-8 max-w-6xl mx-auto overflow-x-auto border border-gray-200"
    >
     <table class="min-w-full divide-y divide-gray-200">
      <thead class="bg-gray-50">
       <tr>
        <th
          class="px-8 py-4 text-left text-xs font-semibold text-gray-500 uppercase tracking-wider"
          scope="col"
        >
         Submission ID
        </th>
        <th
          class="px-8 py-4 text-left text-xs font-semibold text-gray-500 uppercase tracking-wider"
          scope="col"
        >
         Submitted At
        </th>
        <th
          class="px-8 py-4 text-left text-xs font-semibold text-gray-500 uppercase tracking-wider"
          scope="col"
        >
         Answers Summary
        </th>
       </tr>
      </thead>
      <tbody class="bg-white divide-y divide-gray-200" id="submissions-list"></tbody>
     </table>
    </div>
   </section>
  </main>
  <footer
    class="bg-white border-t border-gray-300 py-6 text-center text-gray-600 text-sm tracking-wide"
  >
   © 2024 Form Builder Pro. All rights reserved.
  </footer>
  <script>
   // Note: ERR_NGROK_3200 means your ngrok tunnel is offline or unreachable.
   // To fix this, ensure your local ngrok agent is running and your endpoint is active.
   // This script does not control ngrok tunnels; start ngrok with:
   // ngrok http [your-port] --authtoken 30zoGOK8948uMUj9nflDD3LWuEV_6ShDsrKaG6LgbGDzBC6x4
   // outside of this app in your terminal or server environment.

   // Mobile menu toggle
   const mobileMenuButton = document.getElementById("mobile-menu-button");
   const mobileMenu = document.getElementById("mobile-menu");
   mobileMenuButton.addEventListener("click", () => {
    mobileMenu.classList.toggle("hidden");
   });

   // Data structures
   let formId = null; // will hold saved form ID from backend
   let questions = [];
   let editingQuestionId = null;
   let submissions = [];

   // DOM elements
   const questionsList = document.getElementById("questions-list");
   const questionForm = document.getElementById("question-form");
   const questionTextInput = document.getElementById("question-text");
   const questionTypeSelect = document.getElementById("question-type");
   const optionsContainer = document.getElementById("options-container");
   const optionsList = document.getElementById("options-list");
   const addOptionBtn = document.getElementById("add-option-btn");
   const imageUploadContainer = document.getElementById("image-upload-container");
   const imageUploadInput = document.getElementById("image-upload");
   const imagePreview = document.getElementById("image-preview");
   const questionEditorTitle = document.getElementById("question-editor-title");
   const cancelEditBtn = document.getElementById("cancel-edit-btn");
   const saveFormBtn = document.getElementById("save-form-btn");
   const formPreview = document.getElementById("form-preview");
   const submitAnswersBtn = document.getElementById("submit-answers-btn");
   const submissionsList = document.getElementById("submissions-list");

   // Helpers
   function createOptionInput(value = "") {
    const li = document.createElement("li");
    li.className = "flex items-center space-x-3";

    const input = document.createElement("input");
    input.type = "text";
    input.required = true;
    input.value = value;
    input.className =
     "flex-grow border border-gray-300 rounded-lg px-3 py-2 focus:outline-none focus:ring-4 focus:ring-green-400 transition duration-200";

    const removeBtn = document.createElement("button");
    removeBtn.type = "button";
    removeBtn.className =
     "text-red-600 hover:text-red-800 transition p-2 rounded-lg focus:outline-none focus:ring-4 focus:ring-red-500";
    removeBtn.innerHTML = '<i class="fas fa-times fa-sm"></i>';
    removeBtn.addEventListener("click", () => {
     optionsList.removeChild(li);
    });

    li.appendChild(input);
    li.appendChild(removeBtn);
    return li;
   }

   function resetQuestionForm() {
    questionForm.reset();
    optionsList.innerHTML = "";
    imagePreview.innerHTML = "";
    editingQuestionId = null;
    questionEditorTitle.textContent = "Add New Question";
    cancelEditBtn.classList.add("hidden");
    optionsContainer.classList.add("hidden");
    imageUploadContainer.classList.add("hidden");
   }

   function renderQuestions() {
    questionsList.innerHTML = "";
    if (questions.length === 0) {
     const emptyMsg = document.createElement("p");
     emptyMsg.className = "text-gray-500 italic";
     emptyMsg.textContent = "No questions added yet.";
     questionsList.appendChild(emptyMsg);
     return;
    }
    questions.forEach((q) => {
     const li = document.createElement("li");
     li.className =
      "border border-gray-300 rounded-xl p-5 flex flex-col sm:flex-row sm:items-center sm:justify-between shadow-sm hover:shadow-md transition duration-300";

     const leftDiv = document.createElement("div");
     leftDiv.className = "flex items-center space-x-4 mb-4 sm:mb-0";

     if (q.type === "image" && q.imageUrl) {
      const img = document.createElement("img");
      img.src = q.imageUrl;
      img.alt = `Uploaded image for question: ${q.text}`;
      img.className =
       "h-14 w-14 object-cover rounded-lg border border-gray-300 shadow-sm";
      leftDiv.appendChild(img);
     } else {
      const icon = document.createElement("i");
      icon.className = "fas fa-question-circle text-blue-700 text-2xl";
      leftDiv.appendChild(icon);
     }

     const textDiv = document.createElement("div");
     textDiv.className = "text-gray-900 font-semibold text-lg";
     textDiv.textContent = q.text;
     leftDiv.appendChild(textDiv);

     li.appendChild(leftDiv);

     const rightDiv = document.createElement("div");
     rightDiv.className = "flex space-x-5";

     const editBtn = document.createElement("button");
     editBtn.type = "button";
     editBtn.className =
      "text-yellow-600 hover:text-yellow-800 focus:outline-none focus:ring-4 focus:ring-yellow-500 rounded-lg p-2";
     editBtn.title = "Edit Question";
     editBtn.innerHTML = '<i class="fas fa-edit fa-lg"></i>';
     editBtn.addEventListener("click", () => {
      startEditingQuestion(q.id);
     });

     const deleteBtn = document.createElement("button");
     deleteBtn.type = "button";
     deleteBtn.className =
      "text-red-600 hover:text-red-800 focus:outline-none focus:ring-4 focus:ring-red-500 rounded-lg p-2";
     deleteBtn.title = "Delete Question";
     deleteBtn.innerHTML = '<i class="fas fa-trash-alt fa-lg"></i>';
     deleteBtn.addEventListener("click", () => {
      if (
       confirm(
        "Are you sure you want to delete this question? This action cannot be undone."
       )
      ) {
       questions = questions.filter((item) => item.id !== q.id);
       renderQuestions();
       renderFormPreview();
       resetQuestionForm();
      }
     });

     rightDiv.appendChild(editBtn);
     rightDiv.appendChild(deleteBtn);

     li.appendChild(rightDiv);

     questionsList.appendChild(li);
    });
   }

   function startEditingQuestion(id) {
    const q = questions.find((item) => item.id === id);
    if (!q) return;
    editingQuestionId = id;
    questionEditorTitle.textContent = "Edit Question";
    cancelEditBtn.classList.remove("hidden");

    questionTextInput.value = q.text;
    questionTypeSelect.value = q.type;

    if (q.type === "radio" || q.type === "checkbox" || q.type === "select") {
     optionsContainer.classList.remove("hidden");
     optionsList.innerHTML = "";
     q.options.forEach((opt) => {
      optionsList.appendChild(createOptionInput(opt));
     });
    } else {
     optionsContainer.classList.add("hidden");
     optionsList.innerHTML = "";
    }

    if (q.type === "image") {
     imageUploadContainer.classList.remove("hidden");
     imagePreview.innerHTML = "";
     if (q.imageUrl) {
      const img = document.createElement("img");
      img.src = q.imageUrl;
      img.alt = `Uploaded image for question: ${q.text}`;
      img.className = "max-h-52 rounded-lg border border-gray-300 shadow-sm";
      imagePreview.appendChild(img);
     }
    } else {
     imageUploadContainer.classList.add("hidden");
     imagePreview.innerHTML = "";
    }
   }

   function renderFormPreview() {
    formPreview.innerHTML = "";
    if (questions.length === 0) {
     const p = document.createElement("p");
     p.className = "text-gray-500 italic text-center";
     p.textContent = "No questions to display.";
     formPreview.appendChild(p);
     return;
    }

    questions.forEach((q, idx) => {
     const wrapper = document.createElement("div");
     wrapper.className = "space-y-2";

     const label = document.createElement("label");
     label.className = "block text-gray-900 font-semibold text-lg";
     label.htmlFor = `question-${q.id}`;
     label.textContent = `${idx + 1}. ${q.text}`;
     wrapper.appendChild(label);

     if (q.type === "text") {
      const input = document.createElement("input");
      input.type = "text";
      input.id = `question-${q.id}`;
      input.name = q.id;
      input.required = true;
      input.autocomplete = "off";
      input.className =
       "w-full border border-gray-300 rounded-lg px-4 py-3 focus:outline-none focus:ring-4 focus:ring-blue-400 transition duration-200";
      wrapper.appendChild(input);
     } else if (q.type === "textarea") {
      const textarea = document.createElement("textarea");
      textarea.id = `question-${q.id}`;
      textarea.name = q.id;
      textarea.required = true;
      textarea.rows = 5;
      textarea.className =
       "w-full border border-gray-300 rounded-lg px-4 py-3 focus:outline-none focus:ring-4 focus:ring-blue-400 transition duration-200 resize-y";
      wrapper.appendChild(textarea);
     } else if (q.type === "radio") {
      q.options.forEach((opt, i) => {
       const optionId = `question-${q.id}-option-${i}`;
       const div = document.createElement("div");
       div.className = "flex items-center space-x-3";

       const input = document.createElement("input");
       input.type = "radio";
       input.id = optionId;
       input.name = q.id;
       input.value = opt;
       input.required = true;
       input.className = "focus:ring-blue-500 text-blue-600";

       const labelOpt = document.createElement("label");
       labelOpt.htmlFor = optionId;
       labelOpt.className = "text-gray-800";
       labelOpt.textContent = opt;

       div.appendChild(input);
       div.appendChild(labelOpt);
       wrapper.appendChild(div);
      });
     } else if (q.type === "checkbox") {
      q.options.forEach((opt, i) => {
       const optionId = `question-${q.id}-option-${i}`;
       const div = document.createElement("div");
       div.className = "flex items-center space-x-3";

       const input = document.createElement("input");
       input.type = "checkbox";
       input.id = optionId;
       input.name = q.id;
       input.value = opt;
       input.className = "focus:ring-blue-500 text-blue-600";

       const labelOpt = document.createElement("label");
       labelOpt.htmlFor = optionId;
       labelOpt.className = "text-gray-800";
       labelOpt.textContent = opt;

       div.appendChild(input);
       div.appendChild(labelOpt);
       wrapper.appendChild(div);
      });
     } else if (q.type === "select") {
      const select = document.createElement("select");
      select.id = `question-${q.id}`;
      select.name = q.id;
      select.required = true;
      select.className =
       "w-full border border-gray-300 rounded-lg px-4 py-3 focus:outline-none focus:ring-4 focus:ring-blue-400 transition duration-200";

      const defaultOption = document.createElement("option");
      defaultOption.value = "";
      defaultOption.textContent = "Select an option";
      defaultOption.disabled = true;
      defaultOption.selected = true;
      select.appendChild(defaultOption);

      q.options.forEach((opt) => {
       const option = document.createElement("option");
       option.value = opt;
       option.textContent = opt;
       select.appendChild(option);
      });
      wrapper.appendChild(select);
     } else if (q.type === "image") {
      const input = document.createElement("input");
      input.type = "file";
      input.id = `question-${q.id}`;
      input.name = q.id;
      input.accept = "image/*";
      input.required = true;
      input.className = "w-full rounded-lg border border-gray-300 px-3 py-2";
      wrapper.appendChild(input);
     }

     formPreview.appendChild(wrapper);
    });
   }

   function renderSubmissions() {
    submissionsList.innerHTML = "";
    if (submissions.length === 0) {
     const tr = document.createElement("tr");
     const td = document.createElement("td");
     td.colSpan = 3;
     td.className =
      "px-8 py-6 whitespace-nowrap text-center text-gray-500 italic font-medium";
     td.textContent = "No submissions yet.";
     tr.appendChild(td);
     submissionsList.appendChild(tr);
     return;
    }

    submissions.forEach((sub) => {
     const tr = document.createElement("tr");

     const idTd = document.createElement("td");
     idTd.className =
      "px-8 py-6 whitespace-nowrap text-sm text-gray-900 font-mono font-semibold";
     idTd.textContent = sub.id;

     const dateTd = document.createElement("td");
     dateTd.className = "px-8 py-6 whitespace-nowrap text-sm text-gray-600";
     const date = new Date(sub.submittedAt);
     dateTd.textContent = date.toLocaleString();

     const answersTd = document.createElement("td");
     answersTd.className =
      "px-8 py-6 whitespace-nowrap text-sm text-gray-700 max-w-3xl truncate";

     // Create a summary string of answers
     const summaryArr = [];
     for (const [qid, answer] of Object.entries(sub.answers)) {
      const q = questions.find((item) => item.id === qid);
      if (!q) continue;
      let ansText = "";
      if (Array.isArray(answer)) {
       ansText = answer.join(", ");
      } else if (
       typeof answer === "string" &&
       answer.startsWith("data:image")
      ) {
       ansText = "[Image Uploaded]";
      } else {
       ansText = answer;
      }
      summaryArr.push(`${q.text}: ${ansText}`);
     }
     answersTd.textContent = summaryArr.join(" | ");

     tr.appendChild(idTd);
     tr.appendChild(dateTd);
     tr.appendChild(answersTd);

     submissionsList.appendChild(tr);
    });
   }

   // Event handlers
   questionTypeSelect.addEventListener("change", () => {
    const val = questionTypeSelect.value;
    if (val === "radio" || val === "checkbox" || val === "select") {
     optionsContainer.classList.remove("hidden");
     imageUploadContainer.classList.add("hidden");
     imagePreview.innerHTML = "";
    } else if (val === "image") {
     optionsContainer.classList.add("hidden");
     optionsList.innerHTML = "";
     imageUploadContainer.classList.remove("hidden");
    } else {
     optionsContainer.classList.add("hidden");
     optionsList.innerHTML = "";
     imageUploadContainer.classList.add("hidden");
     imagePreview.innerHTML = "";
    }
   });

   addOptionBtn.addEventListener("click", () => {
    optionsList.appendChild(createOptionInput());
   });

   imageUploadInput.addEventListener("change", () => {
    const file = imageUploadInput.files[0];
    if (!file) {
     imagePreview.innerHTML = "";
     return;
    }
    const reader = new FileReader();
    reader.onload = (e) => {
     imagePreview.innerHTML = "";
     const img = document.createElement("img");
     img.src = e.target.result;
     img.alt = "Preview of uploaded image for question";
     img.className = "max-h-52 rounded-lg border border-gray-300 shadow-sm";
     imagePreview.appendChild(img);
    };
    reader.readAsDataURL(file);
   });

   cancelEditBtn.addEventListener("click", () => {
    resetQuestionForm();
   });

   questionForm.addEventListener("submit", (e) => {
    e.preventDefault();

    const text = questionTextInput.value.trim();
    const type = questionTypeSelect.value;

    if (!text) {
     alert("Question text is required.");
     return;
    }

    let options = [];
    if (type === "radio" || type === "checkbox" || type === "select") {
     const optionInputs = optionsList.querySelectorAll('input[type="text"]');
     options = Array.from(optionInputs)
      .map((input) => input.value.trim())
      .filter((val) => val.length > 0);
     if (options.length < 2) {
      alert("Please provide at least two options.");
      return;
     }
    }

    let imageUrl = null;

    if (type === "image") {
     if (editingQuestionId) {
      // If editing, keep existing image if no new file selected
      if (imageUploadInput.files.length > 0) {
       // Read new image as base64
       const file = imageUploadInput.files[0];
       const reader = new FileReader();
       reader.onload = (event) => {
        imageUrl = event.target.result;
        saveQuestion(text, type, options, imageUrl);
       };
       reader.readAsDataURL(file);
       return; // wait for async read
      } else {
       // Keep existing imageUrl from question
       const existingQ = questions.find((q) => q.id === editingQuestionId);
       imageUrl = existingQ ? existingQ.imageUrl : null;
      }
     } else {
      if (imageUploadInput.files.length === 0) {
       alert("Please upload an image.");
       return;
      }
      const file = imageUploadInput.files[0];
      const reader = new FileReader();
      reader.onload = (event) => {
       imageUrl = event.target.result;
       saveQuestion(text, type, options, imageUrl);
      };
      reader.readAsDataURL(file);
      return; // wait for async read
     }
    }

    saveQuestion(text, type, options, imageUrl);
   });

   function saveQuestion(text, type, options, imageUrl) {
    if (editingQuestionId) {
     // Edit existing
     questions = questions.map((q) => {
      if (q.id === editingQuestionId) {
       return {
        ...q,
        text,
        type,
        options: options.length > 0 ? options : [],
        imageUrl: imageUrl || null,
       };
      }
      return q;
     });
    } else {
     // Add new
     const newQuestion = {
      id: crypto.randomUUID(),
      text,
      type,
      options: options.length > 0 ? options : [],
      imageUrl: imageUrl || null,
     };
     questions.push(newQuestion);
    }
    renderQuestions();
    renderFormPreview();
    resetQuestionForm();
   }

   saveFormBtn.addEventListener("click", async () => {
    if (questions.length === 0) {
     alert("Add at least one question before saving the form.");
     return;
    }
    try {
     saveFormBtn.disabled = true;
     saveFormBtn.innerHTML =
      '<i class="fas fa-spinner fa-spin mr-3"></i>Saving...';

     // Simulate backend save with timeout and generate a fake formId
     await new Promise((resolve) => setTimeout(resolve, 1000));
     formId = crypto.randomUUID();

     alert("Form saved successfully! Form ID: " + formId);
    } catch (error) {
     alert("Error saving form: " + error.message);
    } finally {
     saveFormBtn.disabled = false;
     saveFormBtn.innerHTML =
      '<i class="fas fa-save mr-3"></i><span>Save Form</span>';
    }
   });

   submitAnswersBtn.addEventListener("click", async () => {
    if (!formId) {
     alert("Please save the form first before submitting answers.");
     return;
    }
    const formData = new FormData(formPreview);
    const answers = {};

    for (const q of questions) {
     if (q.type === "checkbox") {
      const values = formData.getAll(q.id);
      if (values.length === 0) {
       alert(`Please answer the question: "${q.text}"`);
       return;
      }
      answers[q.id] = values;
     } else if (q.type === "image") {
      const fileInput = formPreview.querySelector(`[name="${q.id}"]`);
      if (!fileInput || !fileInput.files[0]) {
       alert(`Please upload an image for question: "${q.text}"`);
       return;
      }
      // Convert image file to base64 string
      answers[q.id] = await new Promise((resolve) => {
       const reader = new FileReader();
       reader.onload = (e) => resolve(e.target.result);
       reader.readAsDataURL(fileInput.files[0]);
      });
     } else {
      const val = formData.get(q.id);
      if (!val) {
       alert(`Please answer the question: "${q.text}"`);
       return;
      }
      answers[q.id] = val;
     }
    }

    try {
     submitAnswersBtn.disabled = true;
     submitAnswersBtn.innerHTML =
      '<i class="fas fa-spinner fa-spin mr-3"></i>Submitting...';

     // Simulate backend submission with timeout and generate fake submission id and date
     await new Promise((resolve) => setTimeout(resolve, 1000));
     const submissionId = crypto.randomUUID();
     const submittedAt = new Date().toISOString();

     submissions.push({
      id: submissionId,
      submittedAt,
      answers,
     });
     alert("Answers submitted successfully!");
     renderSubmissions();
     formPreview.reset();
    } catch (error) {
     alert("Error submitting answers: " + error.message);
    } finally {
     submitAnswersBtn.disabled = false;
     submitAnswersBtn.innerHTML =
      '<i class="fas fa-paper-plane mr-3"></i><span>Submit Answers</span>';
    }
   });

   // Add question button clears form for new question
   document.getElementById("add-question-btn").addEventListener("click", () => {
    resetQuestionForm();
   });

   // Initial render
   renderQuestions();
   renderFormPreview();
   renderSubmissions();
  </script>
 </body>
</html>
