**Test Cases Overview**

This section contains five core test cases designed for validating the Payment Gateway API.
Each test focuses on functionality, validation, security, and data integrity across payment and refund workflows.

**Test Case 1: Successful Payment Transaction**

Endpoint: POST /api/v1/payments/initiate
Test Data: Valid card details, amount: ₹500

Expected Result:

Status 200 OK

transaction_id generated

Status = "success"

Validation:

Response includes transaction_id, timestamp, and confirmation message.

** Test Case 2: Payment with Invalid Card Number**

Endpoint: POST /api/v1/payments/initiate
Test Data: Invalid card number: 4111-1111-1111-0000

Expected Result:

Status 400 Bad Request

Error: "Invalid card details"

Validation:

Payment should not proceed.

Correct error code and message returned.

** Test Case 3: Refund Request for Completed Transaction**

Endpoint: POST /api/v1/payments/refund
Test Data: Valid transaction_id, refund_amount: ₹250

Expected Result:

Status 200 OK

refund_id generated

Refund status = "initiated"

Validation:

Refund amount matches request.

Original transaction updated with refund details.

**Test Case 4: Payment Status Inquiry**

Endpoint: GET /api/v1/payments/status/{transaction_id}
Test Data: Existing valid transaction_id

Expected Result:

Status 200 OK

Complete transaction details

Validation:

Response includes payment method, amount, timestamp, and status history.

**Test Case 5: Unauthorized API Access**

Endpoint: POST /api/v1/payments/initiate
Test Data: Missing or invalid API key

Expected Result:

Status 401 Unauthorized

Error: "Unauthorized access"

Validation:

Request rejected before processing.

No transaction created.

Security layer behaves as expected.
