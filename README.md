# **Quiz API: Your Go-To Backend for Dynamic Quizzes** 🚀

This project delivers a robust and flexible RESTful API designed to serve educational quiz content, built swiftly using `json-server` on Node.js. It's perfect for powering interactive quiz applications, providing structured data for questions across various topics like HTML, CSS, JavaScript, and Accessibility.

---

## Overview

This backend project provides a lightweight RESTful API for managing quiz data. It leverages `json-server` to quickly spin up a full-featured API from a single `quizzes.json` file, making it ideal for rapid prototyping and development of frontend applications requiring structured quiz content.

## Features

- **json-server**: Enables rapid API prototyping and development with zero coding required for common REST operations.
- **Node.js**: Provides a performant and scalable runtime environment for the API server.
- **Dynamic Quiz Data**: Serves structured quiz data including titles, icons, questions, options, and answers.
- **RESTful Endpoints**: Supports standard HTTP methods (GET, POST, PUT, DELETE) for interacting with quiz resources.

## Getting Started

To get this quiz API up and running on your local machine, follow these simple steps.

### Installation

1.  **Clone the Repository**:
    ```bash
    git clone https://github.com/Isaacayomi/quiz-api.git
    cd quiz-api
    ```
2.  **Install Dependencies**:
    ```bash
    npm install
    ```
3.  **Start the API Server**:
    ```bash
    npm start
    ```
    The API will be available at `http://localhost:10000`.

### Environment Variables

This project does not require any explicit environment variables. The port and data file are configured directly in the `package.json` script.

## API Documentation

The Quiz API exposes several endpoints to interact with the quiz data.

### Base URL

`http://localhost:10000`

### Endpoints

#### GET /quizzes

Retrieves a list of all available quizzes.

**Request**:
No payload required.

**Response**:

```json
[
  {
    "title": "HTML",
    "icon": "./assets/images/icon-html.svg",
    "questions": [
      {
        "question": "What does HTML stand for?",
        "options": [
          "Hyper Trainer Marking Language",
          "Hyper Text Marketing Language",
          "Hyper Text Markup Language",
          "Hyper Text Markup Leveler"
        ],
        "answer": "Hyper Text Markup Language"
      }
      // ... more questions
    ],
    "id": 1
  },
  {
    "title": "CSS",
    "icon": "./assets/images/icon-css.svg",
    "questions": [
      // ... questions
    ],
    "id": 2
  }
]
```

#### GET /quizzes/:id

Retrieves a single quiz by its unique identifier.

**Request**:
No payload required. Replace `:id` with the actual quiz ID (e.g., `http://localhost:10000/quizzes/1`).

**Response**:

```json
{
  "title": "HTML",
  "icon": "./assets/images/icon-html.svg",
  "questions": [
    {
      "question": "What does HTML stand for?",
      "options": [
        "Hyper Trainer Marking Language",
        "Hyper Text Marketing Language",
        "Hyper Text Markup Language",
        "Hyper Text Markup Leveler"
      ],
      "answer": "Hyper Text Markup Language"
    }
    // ... more questions
  ],
  "id": 1
}
```

#### POST /quizzes

Creates a new quiz.

**Request**:

```json
{
  "title": "New Quiz Topic",
  "icon": "./assets/images/icon-new.svg",
  "questions": [
    {
      "question": "Question 1?",
      "options": ["Option A", "Option B"],
      "answer": "Option A"
    }
  ]
}
```

**Response**:

```json
{
  "title": "New Quiz Topic",
  "icon": "./assets/images/icon-new.svg",
  "questions": [
    {
      "question": "Question 1?",
      "options": ["Option A", "Option B"],
      "answer": "Option A"
    }
  ],
  "id": 5
}
```

**Errors**:

- `400 Bad Request`: If the request body is not valid JSON.

#### PUT /quizzes/:id

Replaces an entire existing quiz with new data.

**Request**:
Replace `:id` with the actual quiz ID.

```json
{
  "title": "Updated Quiz Title",
  "icon": "./assets/images/icon-updated.svg",
  "questions": [
    {
      "question": "Updated Question?",
      "options": ["Opt1", "Opt2"],
      "answer": "Opt1"
    }
  ],
  "id": 1
}
```

**Response**:

```json
{
  "title": "Updated Quiz Title",
  "icon": "./assets/images/icon-updated.svg",
  "questions": [
    {
      "question": "Updated Question?",
      "options": ["Opt1", "Opt2"],
      "answer": "Opt1"
    }
  ],
  "id": 1
}
```

**Errors**:

- `404 Not Found`: If the quiz with the given ID does not exist.
- `400 Bad Request`: If the request body is not valid JSON.

#### DELETE /quizzes/:id

Deletes a quiz by its unique identifier.

**Request**:
No payload required. Replace `:id` with the actual quiz ID.

**Response**:

```json
{}
```

**Errors**:

- `404 Not Found`: If the quiz with the given ID does not exist.

#### GET /quizzes/:id/questions

Retrieves the questions for a specific quiz by its ID.

**Request**:
No payload required. Replace `:id` with the actual quiz ID (e.g., `http://localhost:10000/quizzes/1/questions`).

**Response**:

```json
[
  {
    "question": "What does HTML stand for?",
    "options": [
      "Hyper Trainer Marking Language",
      "Hyper Text Marketing Language",
      "Hyper Text Markup Language",
      "Hyper Text Markup Leveler"
    ],
    "answer": "Hyper Text Markup Language"
  },
  {
    "question": "Which of the following is the correct structure for an HTML document?",
    "options": [
      "<html><head></head><body></body></html>",
      "<head><html></html><body></body></head>",
      "<body><head></head><html></html></body>",
      "<html><body></body><head></head></html>"
    ],
    "answer": "<html><head></head><body></body></html>"
  }
  // ... more questions for the specified quiz
]
```

**Errors**:

- `404 Not Found`: If the quiz with the given ID does not exist.

## Usage

Once the API server is running, you can interact with it using any HTTP client (e.g., Postman, Insomnia, or `curl`). Frontend applications can fetch quiz data or update it using standard `fetch` or `XMLHttpRequest` in JavaScript.

**Example: Fetching all quizzes using JavaScript**

```javascript
fetch("http://localhost:10000/quizzes")
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error("Error fetching quizzes:", error));
```

**Example: Fetching HTML quiz questions**

```javascript
fetch("http://localhost:10000/quizzes/1/questions")
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error("Error fetching HTML questions:", error));
```

## Technologies Used

| Technology      | Description                             | Link                                                                       |
| :-------------- | :-------------------------------------- | :------------------------------------------------------------------------- |
| **Node.js**     | JavaScript runtime environment          | [nodejs.org](https://nodejs.org/)                                          |
| **json-server** | Full fake REST API out of any JSON file | [github.com/typicode/json-server](https://github.com/typicode/json-server) |
| **npm**         | Package manager for JavaScript          | [npmjs.com](https://www.npmjs.com/)                                        |

## License

This project is licensed under the ISC License.

## Author Info

**Isaac Ayomide**

---

[![Node.js Version](https://img.shields.io/badge/Node.js-20+-brightgreen)](https://nodejs.org/)
[![NPM Version](https://img.shields.io/badge/npm->=8.0.0-blue)](https://docs.npmjs.com/cli/v8/using-npm/npm)
[![json-server Version](https://img.shields.io/badge/json--server-1.0.0--beta.3-orange)](https://github.com/typicode/json-server)
[![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](https://opensource.org/licenses/ISC)

[![Readme was generated by Dokugen](https://img.shields.io/badge/Readme%20was%20generated%20by-Dokugen-brightgreen)](https://www.npmjs.com/package/dokugen)
