# Automation Exercise Test Plan

## 1. Objective
This test plan covers the core user journeys for the Automation Exercise e-commerce demo site. The goal is to validate critical functionality, stable navigation, and key user flows using Playwright-based browser automation.

## 2. Scope
### In scope
- Home page and public navigation
- Product listing and product details
- Search and category filtering
- User registration and login
- Cart and quantity updates
- Checkout and order placement
- Contact Us form
- Account deletion and logout
- Recommended items and subscription flow
- Basic UI and responsiveness checks across browsers

### Out of scope
- Payment gateway integration beyond the demo flow
- Real backend or third-party service validation outside the site behavior
- Performance benchmarking beyond smoke checks

## 3. Test Strategy
### Approach
- Create smoke tests for the highest-risk, most used flows
- Add regression tests for authentication, cart, and checkout
- Validate visible UI text, navigation, and persistence across browser sessions
- Prefer stable selectors such as role-based and text-based locators when test automation is implemented

### Environments
- Local browser execution in Playwright
- Browser coverage: Chromium, Firefox, WebKit
- Primary test data: generated users and product selections from the site itself

## 4. Risks and Priorities
### High priority
- Registration/login flow
- Add-to-cart and quantity management
- Checkout and order completion
- Contact form and critical page routing

### Medium priority
- Category and brand filtering
- Product review / recommended items
- Subscription form validation

### Low priority
- Cosmetic layout differences
- Non-critical static content checks

## 5. Test Data
Use data that is easy to create and clean up:
- Unique email for each registration test
- Known product names: Blue Top, Men Tshirt, Summer White Top
- Standard user account credentials for valid/invalid login scenarios
- Valid contact info for form submission tests

## 6. Test Suites

### Suite A: Home and Navigation
- A01: Home page loads successfully and shows key sections
- A02: Header navigation links work correctly
- A03: Category and brand section links open valid product pages
- A04: Footer subscription form accepts valid email input
- A05: Recommended items are visible on the home page under expected conditions

### Suite B: Product Browsing
- B01: Products page loads with multiple product cards
- B02: Product card contains name, price, image, and view button
- B03: Product details page opens with correct name, price, and description
- B04: Search/filter returns relevant products
- B05: Category and brand filters narrow the product list appropriately

### Suite C: Authentication
- C01: Sign up with valid details creates an account successfully
- C02: Sign up with duplicate email shows an error
- C03: Login with valid credentials works
- C04: Login with invalid credentials shows an error message
- C05: Logout ends the active session and redirects appropriately
- C06: Delete account removes the user and prevents login

### Suite D: Cart and Checkout
- D01: Add a product to cart from product listing
- D02: Add product from product details page
- D03: Cart updates quantity and total correctly
- D04: Remove product from cart works as expected
- D05: Proceed to checkout with logged-in user completes order
- D06: Checkout with empty cart blocks purchase and shows a relevant message

### Suite E: Contact and Support
- E01: Contact Us form submits successfully with valid data
- E02: Contact Us form validation blocks empty required fields
- E03: Contact form success message appears after submission

### Suite F: Regression / UI Stability
- F01: Navigation remains intact after multiple page transitions
- F02: Page elements remain visible after reloads
- F03: Browser back/forward navigation keeps valid state
- F04: Error states and empty states are handled gracefully

## 7. Detailed Test Cases

### A01 – Home page loads successfully
- Open the homepage
- Verify the page title and logo are displayed
- Confirm primary sections such as category, feature items, and subscription exist
- Assert no layout-breaking errors occur

### A02 – Header navigation works
- Click each main nav item
- Verify destination pages load without errors
- Confirm expected headings or page elements are visible

### B01 – Products page lists products
- Open the Products page
- Ensure multiple product cards render
- Confirm each product includes image, price, and product name
- Verify pagination or product count behavior if applicable

### B02 – Product detail page displays correct data
- Open a product detail view from the listing
- Confirm product name, price, and category are correct
- Verify quantity selector and Add to cart button are available

### C01 – User registration success
- Navigate to Signup / Login
- Fill valid first name, last name, email, and password
- Submit the form
- Verify account creation confirmation and the account dashboard state

### C02 – Duplicate email registration
- Attempt to register with an already-used email
- Verify the site shows a clear error message
- Confirm the user is not created twice

### C03 – Login success
- Enter valid credentials
- Submit login form
- Verify the user is signed in and redirected to the expected page

### C04 – Login failure
- Enter invalid email/password
- Validate the error state and no session is created

### D01 – Add to cart from product listing
- Select a product from the Products page
- Click Add to cart
- Confirm the modal or confirmation state appears
- Open the cart and validate the item is present

### D02 – Update cart quantity
- Increase or decrease a cart item quantity
- Verify price total updates appropriately
- Confirm the final quantity matches the update

### D03 – Remove an item from cart
- Remove one item from the cart
- Assert the item disappears from the list
- Verify the order total updates correctly

### D05 – Place order
- Add items to cart
- Log in if required
- Proceed to checkout
- Enter valid address and payment details
- Confirm order is placed successfully and success confirmation is shown

### E01 – Contact Us form submission
- Fill the contact fields with valid data
- Upload a file if the form supports it
- Submit the form
- Validate the success confirmation message appears

## 8. Entry and Exit Criteria
### Entry criteria
- The website is reachable and stable
- Browser test environment is configured
- Test data can be created or reset without side effects

### Exit criteria
- All smoke tests pass
- No critical severity issue remains open
- Authentication, cart, and checkout flows are validated in at least one browser pass

## 9. Suggested Playwright Priorities
Recommended execution order:
1. Smoke: homepage, products, login, cart, checkout
2. Regression: registration, contact us, logout, delete account
3. Cross-browser validation: Chromium, Firefox, WebKit

## 10. Acceptance Criteria for Automation
The automation suite is considered complete when:
- Core user journeys can be executed repeatedly without manual intervention
- Clear assertions validate user-visible states
- Test failures provide actionable error messages
- The suite can run locally with Playwright and supports CI-friendly execution

## 11. Recommended Next Step
Start automation with these five smoke tests:
- Home page loads
- User registration and login
- Add product to cart
- Complete checkout flow
- Contact Us form submission

This gives immediate confidence in the site before expanding into broader UI and regression coverage.
