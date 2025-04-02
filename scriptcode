function sendWhatsAppMessage() {
  const spreadsheetId = '1oos3UXcgO9eTdWD8Tf4EUMwe9wOnzgVo99npLnmIfq4';
  const spreadsheet = SpreadsheetApp.openById(spreadsheetId);
  Logger.log("Spreadsheet opened: " + spreadsheet.getName());

  const sheet = spreadsheet.getSheetByName('satclub'); // Check the sheet name
  // if (!sheet) {
  //   Logger.log("Sheet 'contactfile' not found.");
  //   return; // Exit the function if the sheet is not found
  // }

  Logger.log("Spreadsheet accessed successfully.");
  const data = spreadsheet.getDataRange().getValues(); // Get all data

   const sortedData = data.slice(1).sort((a, b) => new Date(b[0]) - new Date(a[0]));
  const latestRow = sortedData[0]; // Most recent entry

  Logger.log("🕒 Most Recent Entry: " + JSON.stringify(latestRow));

   const mobileNumber = latestRow[3];// Adjust column index based on your sheet (e.g., 1 for column B)

  const name = latestRow[1];
  Logger.log("📞 Extracted Mobile Number: " + mobileNumber + "Name" + name);
  const message = `Dear ${name} ji

Greetings from RICH System Solutions Pvt. Ltd.! 👋  

🎊 Wishing You a Prosperous New Financial Year! 🎊
Thank you for filling out the Saturday Club form!

Empowering 2000+ clients since 2009 with smart business automation tools.  

Our Key Services:
✅ Lead Generation & Automation  
✅ Verified WhatsApp API (Blue Tick)  
✅ WhatsApp Chatbots & Promotions  
✅ Personal WhatsApp Services  
✅ Bulk SMS & SMS DLT Management  
✅ AI-Based Business Tools  
✅ Voice Call & IVR Services  
✅ Custom Automation & Software Solutions

📞 Call us: 9921753001 / 9595902003  
📧 support@richsol.com  
🌐 https://www.richsol.com

Let’s grow your business, the smart way! 🚀`;
  const accountSID = ""; // Replace with your Twilio Account SID
  const authToken = ""; // Replace with your Twilio Auth Token
  const url = `https://message.richsol.com/api/v1/sendmessage`;

  const payload = {
    key: 'EXQ159HUKORICHSOLIVDT3YV68',
    mobileno: `${mobileNumber}`, // For International use Country Code
    msg: `${message}`,
    type: 'Text' // Text
  };

  const options = {
    method: "post",
    payload: payload,
    headers: {
      Authorization: "Basic " + Utilities.base64Encode(accountSID + ":" + authToken),
    },
  };

  const response = UrlFetchApp.fetch(url, options);
  const responseCode = response.getResponseCode();
  const responseBody = response.getContentText();

  
  if (responseCode === 201) {
    Logger.log("Message sent successfully!");
  } else {
    Logger.log(`Error: ${responseCode}`);
    Logger.log(`Response: ${responseBody}`);
  }
}
