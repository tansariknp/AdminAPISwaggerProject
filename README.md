# AdminAPISwaggerProject

Application Swagger URL : http://rest-api.upskills.in/doc/admin/

Test Case ID	Test Case Description	Pre-Condition	Test Step	Test Data	Expected Result	Note
TC_001	To verify whether application allows the admin to get access token 	"HEADER 
Authorization: Basic dXBza2lsbHNfcmVzdF9hZG1pbl9vYXV0aF9jbGllbnQ6dXBza2lsbHNfcmVzdF9hZG1pbl9vYXV0aF9zZWNyZXQ=
"	"In Token service, call get access token api endpoint.
POST /oauth2/token/client_credentials"		"Response body with access token details and status code 200 should be get displayed. 
"	
			Add script Assertion to validate status code 	200	Script assertion should be get displayed	
			Run the Test Case		Test Case with assertion should be get displayed as pass	
						
TC_002	"TO verify whether application allows the admin to login into the system with valid credentials and get admin account details  

And log out of the system "	"HEADER
Authorization: Bearer {access token}"	"In User service, call login admin user api endpoint
POST /login"		Login admin user api endpoint should be get displayed	Use .xls file to get data to /login 
			Provide valid admin user request body	"
  ""username"": ""upskills_admin"",
  ""password"": ""Talent4$$""
"	"Response body with logged in admin user details and status code 200 should get displayed.
"	
			Add script Assertion to validate status code and admin username 	"200
""username"": ""upskills_admin"""	Script assertion should be get displayed	
			"In User service, call get admin user account details api endpoint.
GET /user"		"Response body with admin user account details and status code 200 should get displayed.
"	
			Add script Assertion to validate status code and admin username	"200
""username"": ""upskills_admin"""	Script assertion should be get displayed	
			"In User service, call logout admin user api endpoint.
POST /logout"		"Response body with status code 200 should get displayed.
"	
			Add script Assertion to validate status code	200	Script assertion should be get displayed	
			Run the Test Case		Test Case with assertion should be get displayed as pass	
						
TC_029	"
To verify whether application allows the admin to create new order and then generate invoice number to the order"	"the admin  should be logged in, with valid credentials
HEADER
Authorization: Bearer {access token}"	"create a customer with the URI 
POST /customers"	Refer: in Test Data : TD_001	customer id with 200 response code 	Create .xls file to read the customer and product details and update .xls file with order id and invoice number of respective customer  
			use groovy script to get the response (customer_id) and store it to the custom property			
			"create a  product with the URI 
POST /products"	Refer: in Test Data : TD_002	product id with 200 response code 200	
			use groovy script to get the response product id and store it to custom property			
			"create an order for the given customer and products  
POST /orderadmin"	Refer: in Test Data : TD_0010	order id  with response code 200	
			"generate invoice number to the orders 
POST /orders/invoice/{order id}"	101	response code of 200, and invoice number will be genrated	
			Add script Assertion to validate status code	200	Script assertion should be get displayed	
			Run the Test Case		Test Case with assertion should be get displayed as pass	
						
