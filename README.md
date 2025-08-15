# WhatsApp API

A powerful Node.js API solution for seamless WhatsApp messaging and media sharing capabilities. This project leverages the innovators-bot2 package to provide a robust interface for WhatsApp message automation.

## Prerequisites

- [Node.js (v20 or higher)](https://nodejs.org/dist/v20.9.0/node-v20.9.0-x64.msi) - Download and install the latest LTS version
- npm (Node Package Manager) - Included with Node.js installation
- A valid WhatsApp account for the bot
- A valid license from the license manager

## Installation

1. Clone the repository:
```bash
git clone innovatorssoft/WhatsAppAPI
```
```bash
cd WhatsAppAPI
```

2. Install dependencies:
```bash
npm i
```

3. Start the server:
```bash
node api.js
```

The server will start on [http://localhost:3000](http://localhost:3000) by default.


## API Endpoints

### 1. Send Text Message

Send a text message to a WhatsApp number.

**Endpoint:** `POST /send-message`

**Request Body:**
```json
{
  "number": "1234567890",
  "message": "Hello from WhatsApp API!"
}
```

**cURL Example:**
```bash
curl -X POST http://localhost:3000/send-message \
  -H "Content-Type: application/json" \
  -d '{"number": "1234567890", "message": "Hello from WhatsApp API!"}'
```

### 2. Send Media Message

Send an image with caption to a WhatsApp number.

**Endpoint:** `POST /send-media`

**Request Body:**
```json
{
  "number": "1234567890",
  "file": "/path/to/your/local/image.jpg",
  "caption": "Check out this image!"
}
```

**cURL Example:**
```bash
# For local files, use the absolute path
curl -X POST http://localhost:3000/send-media \
  -H "Content-Type: application/json" \
  -d '{"number": "1234567890", "file": "/path/to/your/local/image.jpg", "caption": "Check this out!"}'
```

### 3. Send Document

Send a document to a WhatsApp number.

**Endpoint:** `POST /sendfile`

**Request Body:**
```json
{
  "number": "1234567890",
  "file": "/path/to/your/local/document.pdf",
  "caption": "Here's the document you requested"
}
```

**cURL Example:**
```bash
# For local files, use the absolute path
curl -X POST http://localhost:3000/sendfile \
  -H "Content-Type: application/json" \
  -d '{"number": "1234567890", "file": "/path/to/your/local/document.pdf", "caption": "Document"}'
```

## Response Format

All endpoints return a JSON response with the following format:

```json
{
  "status": true/false,
  "response": "Response message"
}
```

## Error Handling

- `400 Bad Request`: Missing or invalid request parameters
- `404 Not Found`: The provided number is not registered on WhatsApp
- `500 Internal Server Error`: An error occurred while processing the request

## License

This project requires a valid license to function. The application will validate the license on startup and exit if the license is invalid or expired.

## Notes

- The phone number should be in international format without '+' or '00' at the beginning
- For local media files, provide the absolute file path
- The API will automatically add the WhatsApp domain (@s.whatsapp.net) if not provided in the number
- Make sure to keep your session data secure as it contains authentication information
