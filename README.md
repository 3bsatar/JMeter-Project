# 🧪 Performance Task - JMeter Project


sections:

  - name: UI - AP User Journey

  - browser_used: Firefox
    setup:
      - Configured Firefox proxy settings to match local JMeter proxy port
      - Imported JMeter Root CA certificate into Firefox to enable HTTPS recording
    steps:
      - Navigate to https://petstore.octoperf.com/actions/Catalog.action (Landing Page)
      - Click on Sign In → Register Now
      - Fill registration form → Save
      - Select Fish category → Choose first Product ID
      - Select first Item ID → Add to Cart
      - Update Quantity to 10 → Update Cart
      - Proceed to Checkout → Continue → Confirm
      - Select Pay by Bank Wire
      - Confirm order and validate message: Thank you, your order has been submitted.
    highlights:
      - Parameterized user data for flexibility
      - Added text-based assertions for validation
      - Used HTTP Request Defaults for base configuration
      - Added Constant Timers to simulate realistic delays
      - Included Cache & Cookie Managers for proper state handling

  - name: API - RESTful Booking Flow
    steps:
      - POST: Create token → https://restful-booker.herokuapp.com/auth
      - POST: Create booking → https://restful-booker.herokuapp.com/booking
      - GET: Retrieve all booking IDs
      - PUT: Update booking with ID = 1 (extracted dynamically using JSON Extractor)
      - DELETE: Remove booking where ID = 1
    highlights:
      - Parameterized API requests using Test_Data/api_data.csv
      - Added assertions to validate response content
      - Used JSON Extractor and Regex Extractor for dynamic correlation
      - Managed cookies and session data using Cookie Manager

  - name: Performance Analysis
    configuration:
      users: 2
      duration: 10 minutes
      metrics:
        - Error Percentage ≤ 10%
        - 90% of requests ≤ 3 seconds
        - 99% of requests ≤ 5 seconds
    purpose:
      - Validate stability and responsiveness of both UI and API scripts under light concurrent load

meta:
  - author: Mahmoud Mesalem
  - project_status: Completed
  - category: Performance Testing & Load Profiling

tools_used:
  - Apache JMeter
  - Firefox Browser (with proxy & certificate setup)
  - CSV Data Set Config
  - HTTP Request Defaults
  - Constant Timer
  - Cache & Cookie Managers
  - Assertions
  - jp@gc - Stepping Thread Group
  - jp@gc - Ultimate Thread Group

deliverables:
  - JMeter_Assignment_UI.jmx
  - JMeter_Assignment_API.jmx
  - TestData/Test_data.csv
