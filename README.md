# Backend_code
Backend for the Receipt Extractor. Accepts uploaded receipt images, verifies and extracts key information such as vendor name, date, and total amount using a third-party Receipt Verification API. Returns structured data to the frontend via RESTful endpoints. 

Receipt Extractor Backend
This backend service is part of the Receipt Extractor application. It allows users to upload receipt images, which are processed using an AI model to extract key information such as the vendor, date, currency, and itemized purchase data.

Project Objective
Implement a backend API that:

  Accepts receipt image uploads ('.jpg', '.jpeg', '.png')
  Sends the image to an AI model for extraction
  Returns structured receipt data including:
  • Date
  • Currency (3-letter code)
  • Vendor Name
  • Receipt Items (item name, cost, tax, total)
 Saves the extracted details along with the image
 Verifies the AI model’s response
 Provides an endpoint to expose this functionality
 Includes unit tests for various edge cases



Tasks Completed
   Created a 'extractReceiptDetails' service function
   Accepted only '.jpg', '.jpeg', '.png' formats
   Integrated with AI model (via API/SDK) to extract receipt data
   Verified and persisted response
   Created a 'POST' API endpoint: '/extract-receipt-details'
   Returned ID, date, currency, vendor, items, and image URL
   Wrote unit tests for:
    ✔ Successful extraction
    ✔ Invalid file type
    ✔ Invalid/empty AI response
    ✔ General error ('500')



 Sample Data
 This repository includes a 'sample-receipts/' directory with various receipt images for testing purposes.

 Tech Stack
 NestJS (Node.js Framework)
 Axios or Fetch for API calls
 Multer or similar for image upload handling
 Jest for unit testing
 AI model integration via external API



Running the Project Locally

1. Clone the repository:
git clone https://github.com/YOUR_USERNAME/Backend_code.git  
cd Backend_code  


2. Install dependencies:
npm install  

3. Start the server:
npm run start:dev  

The backend will run at:
[http://localhost:3000]


API Endpoint
POST /extract-receipt-details
Request:
Form-data with field: 'file' (Image file)
Response Example:

json
{
  "id": "abc123",
  "date": "2024-06-01",
  "currency_code": "INR",
  "vendor": { "name": "Spencer's" },
  "line_items": [
    { "description": "Item A", "price": 100, "tax": 10, "total": 110 },
    { "description": "Item B", "price": 200, "tax": 20, "total": 220 }
  ],
  "img_thumbnail_url": "http://example.com/image.jpg"
}

Running Tests
To run unit tests:
npm run test  



