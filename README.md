# utahcarol.github.io
<!DOCTYPE html>
<html>
  <head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link href="https://fonts.googleapis.com/css2?family=Open+Sans&display=swap" rel="stylesheet">
    <style>
      body {
        background-color: white;
        text-align: center;
        font-family: 'Open Sans', sans-serif;
      }
      .container {
        display: flex;
        flex-direction: column;
        align-items: center;
      }
      h1 {
        font-size: 2em;
        margin-top: 50px;
      }
      form {
        margin-top: 50px;
        display: flex;
        flex-direction: column;
        align-items: center;
      }
      input[type="text"] {
        padding: 10px;
        font-size: 1.2em;
        border-radius: 20px;
        border: 1px solid lightgray;
        width: 300px;
        text-align: center;
        margin-bottom: 20px;
      }
      button[type="submit"] {
        padding: 10px 20px;
        font-size: 1.2em;
        background-color: magenta;
        color: white;
        border-radius: 20px;
        border: none;
        cursor: pointer;
      }
      .result {
        margin-top: 50px;
        font-size: 1.2em;
        color: gray;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <h1>Welcome to I Love Prompts!</h1>
      <p>Type in the first word that comes to your mind and I will create a silly poem about the word for you!</p>
      <form>
        <input type="text" id="wordInput">
        <button type="submit" id="submitButton">Inspire me!</button>
      </form>
      <div class="result" id="result"></div>
      <p>This website is for entertainment and inspiration only.</p>
    </div>
    <script>
      const submitButton = document.getElementById('submitButton');
      const wordInput = document.getElementById('wordInput');
      const result = document.getElementById('result');

      submitButton.addEventListener('click', async (event) => {
        event.preventDefault();

        const word = wordInput.value;
        const apiKey = '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';

        try {
          const response = await fetch(`https://api.openai.com/v1/engines/text-davinci/jobs`, {
            method: 'POST',
            headers: {
              'Content-Type': 'application/json',
              'Authorization': `Bearer ${apiKey}`
            },
            body: JSON.stringify({
              prompt: `Generate a silly whimsical poem about the word "${word}". The poem should be funny and silly.`,
              max_tokens:
