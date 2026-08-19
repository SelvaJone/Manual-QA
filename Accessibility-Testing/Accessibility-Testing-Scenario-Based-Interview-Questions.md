# Accessibility Testing – Scenario-Based Interview Questions

## 1. What is Accessibility Testing?

Accessibility Testing verifies whether an application can be used effectively by people with disabilities, including users with:

* Visual disabilities
* Hearing disabilities
* Motor disabilities
* Cognitive disabilities
* Speech disabilities
* Temporary or situational limitations

The goal is to ensure that users can perceive, operate, understand, and interact with the application.

Common accessibility standards and guidelines include:

* WCAG 2.0
* WCAG 2.1
* WCAG 2.2
* Section 508
* ADA-related accessibility expectations
* ARIA specifications

---

# 2. Scenario-Based Accessibility Testing Interview Questions

## Scenario 1: A login page has username, password, and login button. How would you test accessibility?

### Answer

I would verify:

1. Every input has a meaningful accessible name.
2. Labels are associated correctly with inputs.
3. The page can be operated entirely using the keyboard.
4. Tab order is logical.
5. Focus is clearly visible.
6. Password requirements are available to screen-reader users.
7. Validation messages are announced.
8. Login button has a meaningful accessible name.
9. Color is not the only method used to communicate errors.
10. The page works with screen readers such as NVDA, JAWS, or VoiceOver.
11. Text and controls have sufficient color contrast.
12. Browser zoom does not make important content unusable.

---

# 3. Scenario: Error message is displayed only in red

## Question

Would you consider this an accessibility issue?

### Answer

Yes.

Color should not be the only method used to communicate information.

For example:

> Password is incorrect

should be accompanied by meaningful text, an icon with an accessible label, or another non-color indicator.

I would verify the error using:

* Text
* Iconography
* Screen reader announcement
* Appropriate ARIA attributes
* Sufficient contrast

---

# 4. Scenario: The application works with a mouse but not with a keyboard

## Question

How would you report this defect?

### Answer

I would report it as an accessibility defect because users with motor disabilities or users who rely on keyboard navigation may not be able to operate the application.

I would verify:

* Tab navigation
* Shift + Tab navigation
* Enter/Space activation
* Escape behavior
* Arrow-key navigation where applicable
* Focus visibility
* Logical focus order
* No keyboard trap

Example:

> User opens the account menu using the keyboard but cannot move to the menu items.

This would be a significant accessibility issue.

---

# 5. Scenario: A modal dialog opens after clicking "Delete"

## Question

How would you test the modal for accessibility?

### Answer

I would verify:

1. Focus moves into the modal.
2. Focus does not unexpectedly move behind the modal.
3. All controls are keyboard accessible.
4. Modal has an accessible name.
5. Screen reader announces the dialog.
6. Escape closes the modal if expected.
7. Focus returns to the triggering element after closing.
8. Background content cannot accidentally receive keyboard focus.
9. Buttons have meaningful names.
10. Confirmation and cancellation actions are distinguishable.

---

# 6. Scenario: Screen reader reads "button button"

## Question

What could be the problem?

### Answer

The button may not have a meaningful accessible name.

For example:

```html
<button>
    <img src="delete.png">
</button>
```

The screen reader may not understand the purpose of the button.

A better implementation could provide an accessible name such as:

```html
<button aria-label="Delete vehicle">
    <img src="delete.png" alt="">
</button>
```

I would validate the behavior using an actual screen reader rather than relying only on DOM inspection.

---

# 7. Scenario: An icon is used instead of text

## Question

How would you test it?

### Answer

I would determine whether the icon communicates meaningful information or is purely decorative.

For meaningful icons:

* Provide an accessible name.
* Verify screen-reader output.
* Ensure sufficient contrast.
* Ensure keyboard accessibility if interactive.
* Verify tooltip behavior if required.

For decorative icons:

* They should generally be hidden from assistive technology.

---

# 8. Scenario: Image has no alternative text

## Question

Is this always a defect?

### Answer

Not always.

If the image communicates meaningful information, it should have appropriate alternative text.

Example:

```html
<img src="vehicle-status.png" alt="Vehicle battery level is 80 percent">
```

For decorative images, an empty alt attribute may be appropriate:

```html
<img src="divider.png" alt="">
```

I would determine the purpose of the image before raising a defect.

---

# 9. Scenario: An e-commerce product image contains important information

## Question

How would you test it?

### Answer

I would verify that the important information is available to screen-reader users.

For example, if the image communicates:

> Red Nike running shoe with white sole

the alternative text should communicate meaningful product information.

I would also verify:

* Product name
* Product price
* Availability
* Ratings
* Promotional information
* Product options

All important information should be accessible without depending solely on the image.

---

# 10. Scenario: A product filter uses checkboxes

## Question

How would you accessibility-test the filters?

### Answer

I would verify:

* Each checkbox has an accessible name.
* Checkbox state is announced.
* Keyboard navigation works.
* Focus is visible.
* Selected/unselected state is communicated.
* Dynamic result updates are accessible.
* Screen readers can understand the filter category.
* Disabled options are announced correctly.

---

# 11. Scenario: Search results update dynamically

## Question

What accessibility checks would you perform?

### Answer

I would verify that screen-reader users are informed when results change.

For example:

> 24 products found.

could be exposed through an appropriate live-region mechanism.

I would also verify:

* Focus behavior
* Loading announcements
* Error announcements
* Result count
* Updated content
* Keyboard navigation

---

# 12. Scenario: An autocomplete field displays suggestions

## Question

How would you test it?

### Answer

I would verify:

1. Input has an accessible name.
2. Suggestions are keyboard accessible.
3. Arrow keys work correctly.
4. Enter selects the expected suggestion.
5. Escape closes suggestions.
6. Screen reader announces available suggestions.
7. Selected suggestion is communicated.
8. Focus behavior is predictable.
9. Loading state is accessible.
10. No keyboard trap occurs.

---

# 13. Scenario: A dropdown is implemented using a custom `<div>`

## Question

What would you investigate?

### Answer

I would investigate whether the custom control correctly exposes:

* Role
* Name
* State
* Value
* Keyboard behavior
* Focus behavior

Native HTML controls should generally be preferred when possible because they provide built-in accessibility behavior.

If a custom component is required, I would verify appropriate ARIA semantics and keyboard interactions.

---

# 14. Scenario: Tab order is incorrect

## Question

Why is this important?

### Answer

Keyboard users depend on logical navigation order.

For example:

```text
Header
Search
Navigation
Product
Add to Cart
Checkout
```

should not unexpectedly become:

```text
Header
Checkout
Footer
Search
Product
```

An incorrect focus order can make the application difficult or impossible to use.

---

# 15. Scenario: Focus indicator is barely visible

## Question

Would you raise a defect?

### Answer

Yes.

Keyboard users need to know which element currently has focus.

I would verify:

* Focus is always visible.
* Focus indicator has sufficient contrast.
* Focus is not hidden behind another component.
* Focus remains visible at different zoom levels.
* Focus behavior works across browsers.

---

# 16. Scenario: User presses Tab and focus disappears

## Question

What would you do?

### Answer

I would treat this as a serious accessibility issue.

I would determine:

1. Which element received focus.
2. Whether focus moved outside the visible viewport.
3. Whether CSS removed the focus indicator.
4. Whether a modal or overlay is involved.
5. Whether JavaScript moved focus unexpectedly.
6. Whether the issue occurs across browsers.

I would capture the exact keyboard sequence and expected versus actual behavior.

---

# 17. Scenario: A page contains a CAPTCHA

## Question

How would you test accessibility?

### Answer

I would verify that the CAPTCHA has an accessible alternative.

Users should not be forced to complete a visual challenge that they cannot perceive.

I would verify:

* Screen-reader accessibility
* Keyboard operation
* Alternative verification mechanism
* Audio alternative where applicable
* Error handling
* Instructions

---

# 18. Scenario: Color contrast fails

## Question

How would you test color contrast?

### Answer

I would use accessibility tools such as:

* axe
* Lighthouse
* WAVE
* Accessibility Insights
* Browser developer tools
* Color contrast analyzers

I would test:

* Normal text
* Large text
* Buttons
* Links
* Form controls
* Placeholder text
* Icons
* Focus indicators
* Disabled-state presentation where applicable

I would compare the implementation against the applicable WCAG criteria.

---

# 19. Scenario: Placeholder text is being used instead of labels

## Question

Is this an accessibility concern?

### Answer

Potentially, yes.

Placeholder text should not generally replace a persistent form label.

Problems include:

* Information disappears when users type.
* Low contrast.
* Screen-reader behavior may vary.
* Users may forget what information is required.

I would verify that every input has a persistent accessible label.

---

# 20. Scenario: Form contains mandatory fields

## Question

How would you test accessibility?

### Answer

I would verify:

* Required fields are programmatically identified.
* Required information is communicated visually.
* Required information is communicated to screen readers.
* Validation errors identify the affected field.
* Error messages explain how to correct the issue.
* Focus moves appropriately after validation.
* Error messages are announced.

---

# 21. Scenario: Form validation displays "Invalid input"

## Question

Is this sufficient?

### Answer

Usually not.

A useful error message should identify:

* Which field is incorrect.
* What is wrong.
* How to correct it.

For example:

> Date of birth must be entered in MM/DD/YYYY format.

is better than:

> Invalid input.

---

# 22. Scenario: Error message appears at the top of a long form

## Question

What would you test?

### Answer

I would verify that keyboard and screen-reader users can discover the error.

I would check:

* Error summary
* Individual field errors
* Focus movement
* Screen-reader announcement
* Links from error summary to fields
* Correct association between field and error
* Preservation of entered values

---

# 23. Scenario: Screen reader does not announce an error

## Question

How would you investigate?

### Answer

I would inspect:

* ARIA live-region implementation
* `aria-describedby`
* `aria-invalid`
* Focus movement
* DOM updates
* Accessible tree
* Timing of dynamic content

I would reproduce with at least one relevant screen reader/browser combination.

---

# 24. Scenario: User enters an incorrect credit-card number

## Question

How would you test accessibility in an e-commerce application?

### Answer

I would verify:

* Field has an accessible label.
* Input purpose is understandable.
* Required format is communicated.
* Error is associated with the field.
* Error is announced.
* Keyboard operation works.
* Screen reader can identify the field state.
* Card-number instructions are accessible.
* Error does not rely only on color.

---

# 25. Scenario: Insurance application has a multi-step quote form

## Question

How would you test accessibility?

### Answer

I would test:

* Step navigation
* Current-step identification
* Form labels
* Required fields
* Error handling
* Keyboard navigation
* Focus management
* Progress indication
* Screen-reader announcements
* Date pickers
* Dropdowns
* Radio buttons
* Checkboxes
* Review page
* Confirmation page

The current step should be clearly communicated to assistive technologies.

---

# 26. Scenario: Banking application has a transaction table

## Question

How would you accessibility-test it?

### Answer

I would verify:

* Table has an appropriate accessible structure.
* Headers are correctly associated with cells.
* Row and column relationships are understandable.
* Sort controls are accessible.
* Pagination is keyboard accessible.
* Transaction status is not communicated only through color.
* Screen readers can understand important transaction details.

---

# 27. Scenario: Connected-car application displays vehicle status

## Question

How would you test accessibility?

### Answer

I would verify that important vehicle information is not communicated only through color, icons, or visual position.

For example:

> Vehicle battery: 75%

should be available as meaningful text to assistive technology.

I would test:

* Vehicle status
* Lock/unlock status
* Battery information
* Vehicle alerts
* Service notifications
* Subscription status
* Buttons
* Navigation
* Voice-over behavior
* Dynamic status updates

---

# 28. Scenario: Mobile application has a "Lock Vehicle" button

## Question

How would you accessibility-test it?

### Answer

I would verify:

* Accessible name
* VoiceOver/TalkBack support
* Logical swipe navigation
* Focus order
* Sufficient touch target size
* State announcement
* Confirmation message
* Error message
* Dynamic status update

For example, after locking:

> Vehicle is locked.

should be communicated accessibly.

---

# 29. Scenario: Mobile screen has several small buttons

## Question

What would you check?

### Answer

I would check whether interactive elements have an adequate touch target size and sufficient spacing.

I would also verify:

* Screen-reader navigation
* Focus order
* Accessible names
* No accidental activation
* Orientation behavior
* Zoom/text scaling where supported

---

# 30. Scenario: User increases system font size on mobile

## Question

How would you test?

### Answer

I would increase the system font size and verify:

* Text remains readable.
* Content does not overlap.
* Buttons remain usable.
* Important information is not clipped.
* Horizontal scrolling does not become excessive where avoidable.
* Controls remain accessible.
* Dialogs remain usable.

---

# 31. Scenario: User zooms browser to 200%

## Question

What should QA verify?

### Answer

I would verify that:

* Content remains readable.
* Controls remain accessible.
* No important information is hidden.
* Layout adapts appropriately.
* Horizontal scrolling is minimized where applicable.
* Navigation remains usable.
* Modal dialogs remain usable.

---

# 32. Scenario: Video contains important instructions

## Question

How would you accessibility-test it?

### Answer

I would verify:

* Captions
* Audio information
* Transcript where appropriate
* Keyboard-accessible video controls
* Play/pause controls
* Volume controls
* Screen-reader accessibility
* Focus visibility

If visual information is essential and not available through audio, an appropriate alternative should be considered.

---

# 33. Scenario: Audio alert indicates a vehicle warning

## Question

How would you test accessibility?

### Answer

The warning should not depend only on sound.

I would verify that the same information is provided through an accessible visual/textual or other suitable mechanism.

For example:

> Low tire pressure detected.

should be available as meaningful information.

---

# 34. Scenario: Toast notification appears for two seconds

## Question

What accessibility problems might exist?

### Answer

A short-lived notification may disappear before some users can perceive it.

I would verify:

* Screen-reader announcement
* Sufficient display duration
* Keyboard behavior
* Ability to review important information
* Focus behavior
* Whether the message contains critical information

For important actions, users should have enough opportunity to understand the result.

---

# 35. Scenario: Session timeout warning appears

## Question

How would you test accessibility?

### Answer

I would verify:

* Warning is accessible to screen readers.
* Focus behavior is correct.
* Remaining time is communicated.
* User can extend the session when applicable.
* Keyboard users can interact with the dialog.
* Timeout does not unexpectedly destroy user-entered information.

This is particularly important for banking, insurance, healthcare, and enterprise applications.

---

# 36. Scenario: Accessibility testing is required but developers say "the UI looks fine"

## Question

How would you respond?

### Answer

I would explain that visual correctness alone does not establish accessibility.

Accessibility involves:

* Keyboard interaction
* Screen readers
* Accessible names
* Focus management
* Semantic structure
* Contrast
* Dynamic announcements
* Alternative text
* Input relationships

I would demonstrate the issue using an assistive technology or accessibility auditing tool.

---

# 37. Scenario: Automated accessibility scan reports 100% compliance

## Question

Can QA stop manual accessibility testing?

### Answer

No.

Automated tools are useful but cannot identify every accessibility problem.

For example, an automated scanner may detect:

* Missing labels
* Missing alt text
* Contrast problems
* Some ARIA issues

But it may not determine whether:

* The label is meaningful.
* The keyboard flow makes sense.
* The screen-reader experience is understandable.
* Focus moves logically.
* Instructions are actually usable.

Therefore, automated and manual accessibility testing should complement each other.

---

# 38. Scenario: axe reports a missing label

## Question

How would you validate the defect?

### Answer

I would:

1. Identify the affected element.
2. Determine the expected accessible name.
3. Inspect the DOM.
4. Test with keyboard.
5. Test with screen reader.
6. Confirm whether the issue affects actual users.
7. Record browser/device/environment information.
8. Provide evidence and remediation guidance.

---

# 39. Scenario: Accessibility defect occurs only in Safari + VoiceOver

## Question

Would you report it?

### Answer

Yes.

Accessibility compatibility can vary between:

* Browser
* Operating system
* Screen reader
* Mobile platform
* Application version

I would document the exact assistive technology combination and classify the defect according to impact.

---

# 40. Scenario: Accessibility issue works correctly in Chrome but fails in Firefox

## Question

How would you approach it?

### Answer

I would:

1. Reproduce in both browsers.
2. Confirm the same application version.
3. Test using keyboard.
4. Test using relevant assistive technology.
5. Inspect accessibility tree differences.
6. Determine whether it is application code or browser/AT behavior.
7. Check supported-browser requirements.
8. Raise the defect if the affected combination is supported.

---

# 41. Scenario: Screen reader reads content in the wrong order

## Question

What might cause this?

### Answer

Possible causes include:

* Incorrect DOM order
* CSS visual reordering
* Incorrect semantic structure
* Improper ARIA
* Hidden elements
* Incorrect heading structure

I would compare the visual order with the DOM and screen-reader reading order.

---

# 42. Scenario: Page has headings but they are not structured correctly

## Question

Why does heading hierarchy matter?

### Answer

Screen-reader users often navigate pages using headings.

A logical structure might be:

```text
H1 - Vehicle Service
    H2 - Upcoming Service
    H2 - Service History
        H3 - 2026 Service
        H3 - 2025 Service
```

Skipping or misusing headings can make navigation difficult.

---

# 43. Scenario: A page contains multiple "Learn More" links

## Question

Is this accessible?

### Answer

It may be confusing.

Screen-reader users navigating by links may hear:

```text
Learn More
Learn More
Learn More
```

without context.

More descriptive accessible names are preferable, such as:

```text
Learn more about vehicle warranty
Learn more about roadside assistance
Learn more about service plans
```

---

# 44. Scenario: Link opens a new tab

## Question

What would you verify?

### Answer

I would verify that users are not unexpectedly moved to another browsing context.

If a new tab/window is opened, appropriate accessible information should communicate that behavior when necessary.

I would also verify:

* Keyboard behavior
* Focus behavior
* Screen-reader announcement
* Link purpose

---

# 45. Scenario: A date picker is not keyboard accessible

## Question

How would you test it?

### Answer

I would verify:

* Input can be accessed by keyboard.
* Calendar can be opened using keyboard.
* Month/year navigation works.
* Dates can be selected using keyboard.
* Selected date is announced.
* Disabled dates are communicated.
* Current date is distinguishable.
* Focus is visible.
* Screen reader understands calendar structure.

If the custom date picker is inaccessible, I would consider whether a native or simpler accessible implementation is more appropriate.

---

# 46. Scenario: A carousel automatically changes slides

## Question

What accessibility issues could exist?

### Answer

Potential issues include:

* Content changes too quickly.
* Keyboard users cannot control the carousel.
* Screen readers receive unexpected updates.
* Controls lack accessible names.
* Current slide is not communicated.
* Pause/stop functionality is missing where required.

I would verify manual controls and appropriate behavior for assistive technologies.

---

# 47. Scenario: Animation causes accessibility problems

## Question

What would you check?

### Answer

I would verify:

* Users can disable or reduce motion where applicable.
* Animation does not prevent interaction.
* Content does not flash dangerously.
* Important information is not conveyed only through animation.
* Focus remains visible.
* Screen-reader users receive equivalent information.

---

# 48. Scenario: User has difficulty distinguishing colors

## Question

How would you design test scenarios?

### Answer

I would test the application using color-vision simulation tools and verify that important information remains understandable.

Examples:

* Success vs failure
* Available vs unavailable
* Active vs inactive
* Selected vs unselected
* Vehicle status
* Insurance status
* Payment status

Information should not rely exclusively on color.

---

# 49. Scenario: User navigates the entire application using only keyboard

## Question

What would your test flow look like?

### Answer

I would:

1. Open the application.
2. Avoid using the mouse.
3. Navigate using Tab.
4. Use Shift + Tab.
5. Use Enter and Space.
6. Use arrow keys where appropriate.
7. Use Escape where expected.
8. Check every interactive component.
9. Verify focus visibility.
10. Check for keyboard traps.
11. Verify modal behavior.
12. Complete important end-to-end workflows.

---

# 50. Scenario: How would you test an e-commerce checkout for accessibility?

## Answer

I would execute an end-to-end accessibility workflow:

```text
Login
  ↓
Search Product
  ↓
Open Product
  ↓
Select Options
  ↓
Add to Cart
  ↓
View Cart
  ↓
Checkout
  ↓
Enter Address
  ↓
Select Shipping
  ↓
Enter Payment
  ↓
Review Order
  ↓
Place Order
  ↓
Order Confirmation
```

For every step I would verify:

* Keyboard access
* Screen-reader support
* Labels
* Error messages
* Focus management
* Contrast
* Dynamic updates
* Accessible names
* Required fields
* Confirmation messages

---

# 51. Scenario: How would you test an insurance quote application?

## Answer

I would test:

```text
Start Quote
   ↓
Customer Information
   ↓
Vehicle Information
   ↓
Driver Information
   ↓
Coverage Selection
   ↓
Quote Calculation
   ↓
Review
   ↓
Purchase
```

I would focus on:

* Accessible form labels
* Required fields
* Radio buttons
* Checkboxes
* Dropdowns
* Date controls
* Error messages
* Quote updates
* Coverage descriptions
* Dynamic pricing updates
* Keyboard navigation
* Screen-reader announcements

---

# 52. Scenario: How would you test a banking application?

## Answer

I would test:

* Login
* Account dashboard
* Account balance
* Transaction history
* Transfers
* Bill payments
* Beneficiary management
* Statements
* Alerts
* Logout

Special attention should be given to:

* Sensitive information
* Session timeout
* Confirmation messages
* Error handling
* Transaction status
* Keyboard accessibility
* Screen-reader compatibility

---

# 53. Scenario: How would you test a connected-car mobile application?

## Answer

I would create scenarios around:

* Login
* Add vehicle
* Vehicle selection
* Vehicle status
* Lock/unlock
* Remote start
* Vehicle alerts
* Service appointment
* Dealer search
* Subscription information
* Customer consent
* Notifications

For each feature I would verify:

* VoiceOver/TalkBack behavior
* Accessible names
* Focus order
* Dynamic announcements
* Button states
* Error messages
* Touch targets
* Text scaling
* Orientation behavior

---

# 54. Scenario: How would you prioritize accessibility defects?

## Answer

I would consider:

### Critical

The user cannot complete a critical workflow.

Example:

> Keyboard user cannot submit an insurance application.

### High

Major functionality is difficult or impossible for users with disabilities.

Example:

> Screen reader cannot access payment controls.

### Medium

The feature is usable but has significant accessibility barriers.

Example:

> Some dynamic messages are not announced.

### Low

Minor accessibility improvement with limited functional impact.

Example:

> Decorative image has unnecessary alternative text.

Severity should ultimately be based on user impact, business impact, compliance requirements, and affected workflows.

---

# 55. Scenario: Developer says ARIA will fix every accessibility issue

## Question

How would you respond?

### Answer

ARIA is not a replacement for semantic HTML and correct application behavior.

I would follow this general principle:

> Use native HTML semantics whenever possible, and use ARIA when necessary.

For example, a native button:

```html
<button>Submit</button>
```

is preferable to recreating a button using:

```html
<div role="button">Submit</div>
```

because native controls already provide many accessibility behaviors.

---

# 56. Scenario: What is the difference between accessibility and usability?

## Answer

**Accessibility** focuses on whether people with disabilities can use the application.

**Usability** focuses more broadly on how effectively, efficiently, and comfortably users can accomplish tasks.

There is overlap, but they are not identical.

Example:

A confusing checkout page may be a usability issue.

A checkout button that cannot be reached using a keyboard is an accessibility issue.

---

# 57. Scenario: What is WCAG?

## Answer

WCAG stands for:

> Web Content Accessibility Guidelines.

WCAG provides guidelines and success criteria for making web content more accessible.

The major principles are commonly represented by:

```text
POUR
```

### P – Perceivable

Information must be presented in ways users can perceive.

### O – Operable

Users must be able to operate controls.

### U – Understandable

Content and behavior should be understandable.

### R – Robust

Content should work with different user agents and assistive technologies.

---

# 58. Scenario: Explain WCAG conformance levels

## Answer

WCAG commonly defines:

### Level A

Minimum accessibility requirements.

### Level AA

Addresses a broader range of accessibility barriers and is a common target for organizations.

### Level AAA

The highest level, containing additional requirements that may not always be practical for every type of content.

As a QA engineer, I would first understand the project's required conformance level before evaluating defects.

---

# 59. Scenario: What accessibility tools have you used?

## Answer

A senior QA engineer may use a combination of:

### Automated

* axe
* Lighthouse
* WAVE
* Accessibility Insights

### Screen Readers

* NVDA
* JAWS
* VoiceOver
* TalkBack

### Browser Tools

* Chrome DevTools
* Firefox accessibility tools
* Accessibility tree inspection

### Manual Testing

* Keyboard-only navigation
* Zoom testing
* Text scaling
* Contrast validation
* Screen-reader workflows

---

# 60. Scenario: How would you integrate accessibility testing into CI/CD?

## Answer

I would introduce automated accessibility checks into the pipeline.

Example:

```text
Developer Commit
      ↓
Build
      ↓
Unit Tests
      ↓
API Tests
      ↓
UI Tests
      ↓
Accessibility Scan
      ↓
Report
      ↓
Pass / Fail
```

Automated tools such as axe can be integrated with browser automation frameworks.

However, I would not depend exclusively on automated scans.

Manual accessibility testing would remain part of the QA process.

---

# 61. Scenario: How would you integrate accessibility checks into Playwright?

## Answer

A common approach is to use an accessibility scanning library such as axe with Playwright.

Example conceptual flow:

```text
Launch Browser
     ↓
Navigate to Page
     ↓
Run Accessibility Scan
     ↓
Capture Violations
     ↓
Filter Known Exceptions
     ↓
Fail Build for Blocking Violations
     ↓
Generate Report
```

The test should identify:

* Rule violated
* Element
* Impact
* HTML context
* Suggested remediation

---

# 62. Scenario: Accessibility scan generates hundreds of violations

## Question

What would you do?

### Answer

I would not immediately create hundreds of individual defects.

I would:

1. Group violations by rule.
2. Identify common root causes.
3. Identify affected components.
4. Prioritize critical workflows.
5. Separate genuine defects from false positives.
6. Identify reusable component-level fixes.
7. Coordinate with developers.
8. Track remediation.
9. Re-run the scan.
10. Perform manual verification.

For example, one incorrect shared button component may cause hundreds of failures.

Fixing the component can eliminate many violations.

---

# 63. Scenario: Accessibility testing is requested one day before release

## Question

What would you do?

### Answer

I would perform risk-based accessibility testing.

I would prioritize:

1. Login
2. Core navigation
3. Critical business workflows
4. Forms
5. Payment
6. Error handling
7. Modals
8. Keyboard navigation
9. Screen-reader critical flows
10. Known accessibility-sensitive components

I would also run automated scanning against high-risk pages.

I would communicate remaining risk clearly rather than claiming complete accessibility coverage.

---

# 64. Scenario: Product owner asks whether accessibility testing is complete

## Question

How would you answer?

### Answer

I would avoid saying "100% complete" unless the defined scope and acceptance criteria have genuinely been satisfied.

I would report:

* Pages tested
* Devices tested
* Browsers tested
* Assistive technologies tested
* WCAG level targeted
* Automated scan results
* Manual results
* Open defects
* Known limitations
* Residual risk

---

# 65. Scenario: Accessibility defect is fixed

## Question

How would you perform regression?

### Answer

I would verify:

1. Original defect is fixed.
2. Screen-reader behavior is correct.
3. Keyboard behavior remains correct.
4. Visual behavior is unaffected.
5. Related components still work.
6. Responsive layouts remain correct.
7. Other browsers remain supported.
8. Automated accessibility scans no longer report the issue.

I would also test nearby functionality because accessibility fixes can sometimes affect focus, styling, or JavaScript behavior.

---

# 66. Scenario: How would you write an accessibility defect?

## Answer

A good defect should include:

### Title

```text
Keyboard users cannot access the "Submit Quote" button
```

### Environment

```text
Browser: Chrome
OS: Windows
Screen Reader: NVDA
Application Version: x.x.x
```

### Steps

```text
1. Open the insurance quote page.
2. Navigate through the form using Tab.
3. Reach the final section.
4. Continue pressing Tab.
```

### Actual Result

```text
Focus skips the Submit Quote button.
```

### Expected Result

```text
Submit Quote should be reachable and operable using the keyboard.
```

### Impact

```text
Keyboard-only users cannot submit the quote.
```

---

# 67. Scenario: Accessibility defect is rejected as low priority

## Question

How would you defend its importance?

### Answer

I would explain the user impact rather than focusing only on the technical implementation.

For example:

> A keyboard user cannot submit an insurance quote.

That means an entire group of users may be unable to complete a core business workflow.

I would provide:

* Reproduction steps
* Screen recording
* Screen-reader output
* Accessibility rule reference
* Business impact
* Supported-platform information

---

# 68. Scenario: What is a keyboard trap?

## Answer

A keyboard trap occurs when keyboard focus enters a component but the user cannot move focus out using expected keyboard controls.

Example:

```text
Page
 ↓
Modal
 ↓
Focusable element
 ↓
Focus cannot escape
```

This can make the application unusable for keyboard-only users.

---

# 69. Scenario: How would you test a keyboard trap?

## Answer

I would:

1. Start at the page.
2. Navigate only using keyboard.
3. Open every modal/menu/dialog.
4. Continue using Tab and Shift + Tab.
5. Use Escape where expected.
6. Verify focus can leave the component.
7. Verify focus returns to the correct element.

---

# 70. Scenario: What is an accessible name?

## Answer

An accessible name is the name exposed to assistive technologies for an interactive element.

For example:

```html
<button aria-label="Delete vehicle">
    🗑
</button>
```

The accessible name is:

> Delete vehicle

This allows screen-reader users to understand the purpose of the control.

---

# 71. Scenario: What is `aria-label`?

## Answer

`aria-label` provides an accessible name directly when appropriate.

Example:

```html
<button aria-label="Close dialog">
    X
</button>
```

However, it should not be used unnecessarily when visible text already provides a suitable accessible name.

---

# 72. Scenario: What is `aria-describedby`?

## Answer

`aria-describedby` can associate additional descriptive information with an element.

Example:

```html
<input
    aria-describedby="password-help"
    type="password"
/>

<div id="password-help">
    Password must contain at least 12 characters.
</div>
```

A screen reader can use the associated description to provide additional context.

---

# 73. Scenario: What is `aria-invalid`?

## Answer

`aria-invalid` can communicate that a form control has an invalid value.

Example:

```html
<input
    aria-invalid="true"
    aria-describedby="email-error"
/>
```

The associated error should provide useful information about how to correct the problem.

---

# 74. Scenario: How would you test a screen reader workflow?

## Answer

I would:

1. Enable the screen reader.
2. Navigate using keyboard/screen-reader commands.
3. Navigate by headings.
4. Navigate by landmarks.
5. Navigate by links.
6. Navigate by form controls.
7. Listen to accessible names.
8. Verify states and values.
9. Trigger errors.
10. Verify announcements.
11. Test dialogs.
12. Test dynamic content.

I would compare the experience against the intended visual workflow.

---

# 75. Scenario: How would you test accessibility on iOS?

## Answer

I would use VoiceOver and verify:

* Swipe navigation
* Rotor navigation
* Accessible names
* Traits
* Focus order
* Buttons
* Text fields
* Switches
* Alerts
* Dynamic updates
* Navigation
* Modal behavior
* Touch target size
* Dynamic Type
* Orientation

---

# 76. Scenario: How would you test accessibility on Android?

## Answer

I would use TalkBack and verify:

* Swipe navigation
* Explore-by-touch
* Accessibility labels
* Focus order
* Buttons
* Input fields
* Dialogs
* Lists
* Dynamic updates
* Error announcements
* Touch targets
* Text scaling
* Orientation

---

# 77. Scenario: What is the difference between accessibility testing and compatibility testing?

## Answer

### Accessibility Testing

Focuses on whether users with disabilities can use the application.

### Compatibility Testing

Focuses on whether the application works across:

* Browsers
* Operating systems
* Devices
* Screen sizes
* Versions

They can overlap because accessibility behavior can vary across browsers, operating systems, and assistive technologies.

---

# 78. Scenario: What accessibility metrics would you report?

## Answer

Useful metrics include:

* Number of accessibility defects
* Critical accessibility defects
* High-severity defects
* Defects by WCAG principle
* Defects by component
* Automated scan violations
* Manual test coverage
* Keyboard coverage
* Screen-reader coverage
* Accessibility regression pass rate
* Defect closure rate

---

# 79. Scenario: How would you build an accessibility test strategy?

## Answer

I would define:

```text
Accessibility Requirements
        ↓
Supported Platforms
        ↓
WCAG Target
        ↓
Risk Assessment
        ↓
Automated Testing
        ↓
Keyboard Testing
        ↓
Screen Reader Testing
        ↓
Mobile Accessibility Testing
        ↓
Defect Management
        ↓
Regression Testing
        ↓
Accessibility Sign-off
```

The strategy should be introduced early rather than waiting until the end of the release.

---

# 80. Scenario: Accessibility testing for a large enterprise application

## Question

How would you scale accessibility testing?

### Answer

I would establish:

### 1. Accessibility standards

Define required standards and conformance level.

### 2. Automated scanning

Integrate scans into CI/CD.

### 3. Shared component testing

Test common components once and reuse them across applications.

### 4. Manual testing

Perform keyboard and screen-reader testing on critical workflows.

### 5. Device/browser matrix

Define supported combinations.

### 6. Accessibility defect governance

Track defects by severity and business impact.

### 7. Regression

Run accessibility checks for every major release.

---

# 81. Senior-Level Scenario: Developer asks QA to provide exact accessibility requirements

## Answer

I would work from the application's accessibility requirements and applicable standards.

I would identify:

* Required WCAG version
* Required conformance level
* Supported browsers
* Supported operating systems
* Supported mobile platforms
* Required assistive technologies
* Business-critical workflows
* Legal/compliance requirements
* Product-specific accessibility expectations

I would convert those requirements into measurable test conditions.

---

# 82. Senior-Level Scenario: Accessibility testing finds a defect in a shared component

## Question

What would you do?

### Answer

I would investigate the component's usage across the application.

For example:

```text
Shared Date Picker
       ↓
Application A
Application B
Application C
Application D
```

If the component has an accessibility problem, fixing it at the component level may resolve issues across multiple applications.

I would therefore:

1. Identify the root cause.
2. Identify all impacted consumers.
3. Raise or link defects appropriately.
4. Coordinate with the component owner.
5. Regression-test all major consumers.

---

# 83. Senior-Level Scenario: Product uses custom controls everywhere

## Question

How would you approach testing?

### Answer

I would identify reusable custom controls such as:

* Dropdowns
* Date pickers
* Modals
* Tabs
* Accordions
* Carousels
* Autocomplete fields
* Toggle switches

I would create accessibility test coverage for each component and then verify the components in actual business workflows.

This provides better coverage than testing every page independently.

---

# 84. Senior-Level Scenario: Accessibility testing is not included in the sprint definition of done

## Question

What would you recommend?

### Answer

I would recommend adding accessibility acceptance criteria to the Definition of Done.

For example:

```text
Feature is complete only when:

- Keyboard navigation works.
- Focus is visible.
- Accessible names are present.
- Critical screen-reader workflow works.
- Automated accessibility scan passes required rules.
- No unresolved critical accessibility defects exist.
```

This shifts accessibility from a final-phase activity into continuous quality engineering.

---

# 85. Senior-Level Scenario: How would you convince management to invest in accessibility testing?

## Answer

I would explain the value in terms of:

* Inclusive user experience
* Product quality
* Reduced accessibility defects
* Better maintainability
* Regulatory/compliance expectations
* Reduced rework
* Improved component quality
* Better overall usability

I would also demonstrate the user impact of real defects rather than presenting accessibility as only a checklist.

---

# 86. Senior-Level Scenario: Accessibility testing vs shift-left

## Question

How would you apply shift-left accessibility testing?

### Answer

I would introduce accessibility activities throughout development:

### Requirement Phase

Identify accessibility requirements.

### Design Phase

Review keyboard flow, focus, labels, contrast, and component behavior.

### Development Phase

Use accessible semantic HTML and reusable accessible components.

### Unit/Component Phase

Test component accessibility.

### Automation Phase

Run automated scans.

### QA Phase

Perform keyboard and screen-reader testing.

### Regression Phase

Run accessibility checks again.

This reduces the cost of fixing accessibility defects late in the release.

---

# 87. Senior-Level Scenario: What would you include in an accessibility regression suite?

## Answer

I would prioritize reusable and business-critical scenarios:

```text
Login
Navigation
Search
Forms
Error Handling
Modal Dialogs
Tables
Dropdowns
Date Pickers
Dynamic Content
Checkout
Payment
Confirmation
Logout
```

For mobile:

```text
Login
Navigation
Vehicle Selection
Vehicle Status
Remote Actions
Alerts
Service Appointment
Notifications
Account
Logout
```

---

# 88. Scenario: Accessibility defect passes automated testing but fails with VoiceOver

## Question

Why?

### Answer

Automated tools cannot simulate the complete user experience.

The automated scan may verify that an accessible name exists, but it may not determine whether the name is:

* Meaningful
* Correct
* Announced at the right time
* Presented in the correct context

Therefore, manual assistive-technology testing is still necessary.

---

# 89. Scenario: Accessibility testing has limited time

## Question

How would you prioritize?

### Answer

I would use risk-based testing.

### Highest Priority

* Login
* Payment
* Checkout
* Insurance purchase
* Banking transactions
* Vehicle remote actions
* Critical forms
* Navigation
* Error handling

### Medium Priority

* Search
* Filters
* Account settings
* History pages

### Lower Priority

* Informational pages
* Decorative content

The exact priority should depend on business risk and user impact.

---

# 90. Final Interview Scenario: Explain your accessibility testing approach as a Senior QA Engineer

## Answer

I would explain my approach like this:

> "I treat accessibility as part of overall quality rather than a separate testing activity. I start by understanding the accessibility requirements, supported platforms, WCAG target, and critical business workflows. I combine automated tools such as axe, Lighthouse, or WAVE with manual keyboard testing and assistive-technology testing using tools such as NVDA, JAWS, VoiceOver, and TalkBack. I validate accessible names, semantic structure, focus management, keyboard navigation, color contrast, forms, error handling, dynamic content, dialogs, tables, and responsive behavior. For mobile applications, I additionally validate VoiceOver, TalkBack, touch targets, text scaling, and orientation. I integrate automated accessibility checks into CI/CD where practical and use risk-based manual testing for critical workflows. When defects are identified, I focus on root causes, especially shared components, and perform regression testing after fixes. My goal is not simply to achieve a clean automated scan but to ensure that real users using assistive technologies can successfully complete important business workflows."

---

# Accessibility Testing Quick Reference

## Core Areas

| Area            | What QA Should Verify                         |
| --------------- | --------------------------------------------- |
| Keyboard        | Complete application can be operated          |
| Focus           | Visible and logical                           |
| Screen Reader   | Content and controls are understandable       |
| Labels          | Inputs have meaningful accessible names       |
| Images          | Meaningful alternative text                   |
| Contrast        | Text and controls are distinguishable         |
| Forms           | Labels, errors, required states               |
| Modals          | Focus management and announcements            |
| Dynamic Content | Updates are communicated                      |
| Headings        | Logical hierarchy                             |
| Links           | Link purpose is understandable                |
| Buttons         | Accessible names and states                   |
| Tables          | Headers and relationships                     |
| Mobile          | VoiceOver/TalkBack support                    |
| Zoom            | Content remains usable                        |
| Text Scaling    | Content remains readable                      |
| Animation       | Does not create barriers                      |
| Video           | Captions and accessible controls              |
| Alerts          | Important information is not color/sound only |

---

# Accessibility Testing Checklist

* [ ] Verify keyboard-only navigation.
* [ ] Verify visible focus.
* [ ] Verify logical focus order.
* [ ] Check for keyboard traps.
* [ ] Verify accessible names.
* [ ] Verify form labels.
* [ ] Verify required-field identification.
* [ ] Verify validation messages.
* [ ] Verify error announcements.
* [ ] Verify alternative text.
* [ ] Verify heading hierarchy.
* [ ] Verify link purpose.
* [ ] Verify button purpose.
* [ ] Verify color contrast.
* [ ] Verify information is not conveyed by color alone.
* [ ] Verify dynamic content announcements.
* [ ] Verify modal focus management.
* [ ] Verify dropdown accessibility.
* [ ] Verify date-picker accessibility.
* [ ] Verify autocomplete accessibility.
* [ ] Verify table accessibility.
* [ ] Verify carousel accessibility.
* [ ] Verify video captions.
* [ ] Verify browser zoom.
* [ ] Verify text scaling.
* [ ] Verify mobile accessibility.
* [ ] Verify VoiceOver.
* [ ] Verify TalkBack.
* [ ] Verify NVDA where applicable.
* [ ] Run automated accessibility scans.
* [ ] Review automated false positives.
* [ ] Perform manual accessibility testing.
* [ ] Regression-test accessibility fixes.
* [ ] Track accessibility defects by severity and impact.

---

# Key Accessibility Interview Terms

```text
WCAG
POUR
ARIA
Accessible Name
Alternative Text
Keyboard Navigation
Keyboard Trap
Focus Management
Focus Indicator
Screen Reader
NVDA
JAWS
VoiceOver
TalkBack
Color Contrast
Semantic HTML
ARIA Label
ARIA Describedby
ARIA Invalid
Live Region
Responsive Accessibility
Dynamic Content
Accessibility Tree
Section 508
Level A
Level AA
Level AAA
```

---

# Final Takeaway

A strong Senior QA Engineer should not describe accessibility testing as simply:

> "I run an accessibility tool."

A stronger answer is:

```text
Requirements
     ↓
Accessibility Standards
     ↓
Risk Assessment
     ↓
Semantic/UI Review
     ↓
Automated Scanning
     ↓
Keyboard Testing
     ↓
Screen Reader Testing
     ↓
Mobile Accessibility
     ↓
Critical End-to-End Workflows
     ↓
Defect Management
     ↓
Regression
     ↓
Accessibility Sign-off
```

The most important principle is:

> **Accessibility testing should validate the real user's ability to perceive, operate, understand, and successfully complete the application's workflows—not just whether an automated scanner reports violations.**
