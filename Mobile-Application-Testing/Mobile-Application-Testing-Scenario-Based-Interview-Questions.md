# Mobile Application Testing – Scenario-Based Interview Questions

## 1. Your mobile application works correctly on Android but crashes on iOS. How would you investigate?

I would first confirm the issue on the affected iOS version and device model.

I would check:

* iOS version
* Device model
* Application version/build
* Crash logs
* Device logs
* Steps to reproduce
* Network conditions
* Permissions
* Application state
* Whether the issue occurs only on fresh installation or upgrade

I would compare the Android and iOS implementations and provide developers with reproducible steps and logs.

---

## 2. The application crashes immediately after launch. What would you test?

I would verify:

1. Fresh installation.
2. Upgrade from the previous version.
3. Different supported OS versions.
4. Different device models.
5. Available device storage.
6. Network connectivity.
7. Application permissions.
8. Backend availability.
9. Crash logs.
10. Whether clearing application data resolves the issue.

I would determine whether the crash is device-specific, OS-specific, build-specific, or environment-specific.

---

## 3. The application works on Wi-Fi but fails on mobile data. How would you test it?

I would compare:

* Wi-Fi vs cellular network
* Different cellular providers if available
* Strong vs weak signal
* HTTP/HTTPS connectivity
* DNS behavior
* API requests
* Timeout behavior
* Authentication/session behavior
* Backend accessibility

I would inspect network logs and API responses to determine whether the problem is in the mobile application, network configuration, or backend.

---

## 4. What happens if the network changes while an API request is in progress?

I would test scenarios such as:

* Wi-Fi → mobile data
* Mobile data → Wi-Fi
* Connected → airplane mode
* Strong network → weak network
* Network disconnected during upload
* Network disconnected during download
* Network restored after failure

I would verify that the application does not crash, handles timeout/error messages correctly, avoids duplicate transactions, and recovers when connectivity returns.

---

## 5. The application shows a loading spinner indefinitely. How would you debug it?

I would determine whether:

* API request was sent.
* API response was received.
* Response contains valid data.
* API request timed out.
* Backend is unavailable.
* Network connection changed.
* UI failed to process the response.
* Application entered an unexpected state.

I would use application logs, API tools, proxy/network logs, and backend logs where available.

---

## 6. How would you test an application when there are many Android and iOS devices?

I would create a device/OS compatibility matrix.

For example:

| Platform | OS                 | Device Category        |
| -------- | ------------------ | ---------------------- |
| Android  | Current supported  | Low-end                |
| Android  | Current supported  | Mid-range              |
| Android  | Previous supported | High-end               |
| iOS      | Current supported  | Latest                 |
| iOS      | Previous supported | Older supported device |

I would prioritize devices based on:

* Customer usage
* Supported OS versions
* Business criticality
* Historical defects
* Device-specific functionality

---

## 7. How would you test application installation?

I would test:

* Fresh installation
* Installation from store
* Installation from test distribution
* Installation with insufficient storage
* Installation on unsupported OS
* Installation when network is interrupted
* Installation after uninstalling an older version
* Installation over an existing version
* Installation permission behavior

After installation, I would verify launch, permissions, configuration, login, and core functionality.

---

## 8. How would you test application upgrades?

I would verify:

* Old version → new version
* Multiple-version upgrade paths
* Existing logged-in user
* Existing application data
* Existing configuration
* Existing tokens/session
* Database migration
* New permissions
* Removed features
* Changed APIs

I would make sure user data is not unexpectedly lost or corrupted.

---

## 9. What would you test when an application is uninstalled and reinstalled?

I would verify:

* Application data removal
* Login state
* Local cache
* Preferences
* Secure storage
* Database data
* Push notification registration
* Permissions
* First-launch behavior

I would also verify server-side data separately because uninstalling the app should not necessarily remove backend customer data.

---

## 10. How would you test application permissions?

I would test:

* Permission granted
* Permission denied
* Permission denied multiple times
* Permission revoked from device settings
* Permission granted later
* Permission denied permanently
* Application behavior when permission is unavailable

Examples include:

* Location
* Camera
* Microphone
* Notifications
* Bluetooth
* Contacts
* Photos
* Storage

The application should gracefully handle denied permissions.

---

## 11. How would you test push notifications?

I would verify:

* Notification when app is foreground
* Notification when app is background
* Notification when app is closed
* Notification after device restart
* Notification tap behavior
* Deep-link navigation
* Duplicate notifications
* Delayed notifications
* Invalid/expired token
* Notification permissions disabled
* Notification content
* Localization

I would also validate that sensitive information is not improperly exposed in notification text.

---

## 12. A push notification arrives, but tapping it opens the wrong screen. What would you investigate?

I would inspect:

* Notification payload
* Deep-link URL
* Navigation mapping
* User authentication state
* Application state
* Expired notification
* Destination screen availability
* Environment configuration

I would compare the payload received by the device with the expected navigation destination.

---

## 13. How would you test an application in airplane mode?

I would enable airplane mode and verify:

* Application launch
* Cached data
* Offline functionality
* API failures
* Error messages
* Retry functionality
* Data entry
* Data persistence
* Sync behavior after connectivity returns

I would ensure the app does not continuously retry requests and drain battery unnecessarily.

---

## 14. What would you test when the application moves from background to foreground?

I would verify:

* Current screen remains correct.
* Session remains valid.
* Data is refreshed where required.
* Pending operations are handled correctly.
* UI state is preserved.
* API calls are not duplicated.
* Authentication expiration is handled.
* Application does not crash.

I would test short and long background durations.

---

## 15. How would you test an incoming phone call while using the application?

I would:

1. Start an important application flow.
2. Receive a phone call.
3. Answer the call.
4. End the call.
5. Return to the application.
6. Verify application state.

I would also test incoming calls during:

* Video/audio usage
* Payment
* Form submission
* File upload
* API transaction
* Authentication

---

## 16. How would you test SMS interruption?

I would verify application behavior when an SMS notification appears during an active workflow.

I would check:

* UI state
* Data preservation
* Navigation
* Keyboard state
* Transaction state
* Application recovery

---

## 17. How would you test screen rotation?

If rotation is supported, I would test:

* Portrait → landscape
* Landscape → portrait
* Rotation during form entry
* Rotation during API loading
* Rotation during error state
* Rotation during scrolling
* Rotation with keyboard open

I would verify that entered data and application state are preserved.

---

## 18. How would you test an application that should support only portrait mode?

I would attempt rotation and verify that:

* Application remains stable.
* UI does not rotate unexpectedly.
* Content is not clipped.
* Buttons remain accessible.
* Keyboard behavior remains correct.
* Application does not crash.

---

## 19. A text field accepts unexpected characters. How would you test it?

I would test:

* Alphabetic characters
* Numeric characters
* Special characters
* Spaces
* Leading/trailing spaces
* Unicode characters
* Emoji
* Very long input
* Copy/paste
* Newline characters
* SQL/script-like input
* Empty input

I would verify both client-side validation and backend validation.

---

## 20. How would you test a mobile numeric field?

I would verify:

* Numeric keyboard appears.
* Decimal input if applicable.
* Negative values if applicable.
* Maximum length.
* Minimum value.
* Maximum value.
* Leading zeros.
* Copy/paste behavior.
* Alphabetic characters are rejected.
* Special characters are handled correctly.

---

## 21. The keyboard hides an important button. How would you test it?

I would:

* Open the keyboard.
* Enter data into lower fields.
* Scroll the page.
* Switch between fields.
* Test different keyboard types.
* Test different screen sizes.

The application should allow the user to access the field and action button without the keyboard permanently blocking them.

---

## 22. How would you test mobile app localization?

I would test supported:

* Languages
* Regions
* Date formats
* Time formats
* Currency
* Number formats
* Text direction where applicable
* Translated labels
* Error messages
* Notifications
* Buttons
* Dynamic content

I would also check for text truncation and untranslated strings.

---

## 23. The application supports English and Spanish. What scenarios would you test?

I would test:

* Device language = English
* Device language = Spanish
* App language = English
* App language = Spanish
* Switching language while logged in
* Switching language during a workflow
* Notifications
* Error messages
* API-provided messages
* Dates and numbers

I would verify that the entire application consistently follows the selected language.

---

## 24. How would you test date and time functionality?

I would test:

* Different time zones
* Daylight saving changes
* Device date/time changes
* 12-hour format
* 24-hour format
* Past dates
* Future dates
* Leap years
* Month-end dates
* Year-end dates
* Invalid dates

I would compare UI values against backend/API values.

---

## 25. How would you test location-based functionality?

I would test:

* Location permission granted
* Location permission denied
* GPS disabled
* Poor GPS signal
* Different locations
* Location changes while app is running
* Background location
* Fake/mock location where permitted for testing
* Incorrect location
* Location timeout

I would verify that location-dependent business rules work correctly.

---

## 26. How would you test deep links?

I would test deep links when:

* App is closed
* App is in background
* App is already open
* User is logged in
* User is logged out
* Session has expired
* Link is invalid
* Link points to unavailable content

I would verify that the correct screen opens and authentication rules are respected.

---

## 27. A deep link works on Android but not iOS. What would you check?

I would compare:

* Deep-link format
* Universal Links configuration
* Associated Domains
* URL schemes
* Application entitlements
* Payload
* Environment configuration
* Device/browser behavior

I would capture logs and provide the exact failing link and device configuration.

---

## 28. How would you test biometric authentication?

I would test:

* Successful fingerprint authentication
* Failed authentication
* Multiple failures
* Face recognition
* Biometric disabled
* Biometric removed from device
* New biometric added
* Device passcode fallback
* Application reinstall
* Session expiration

I would also verify that sensitive operations require appropriate authentication.

---

## 29. How would you test session timeout in a mobile application?

I would:

1. Log in.
2. Leave the application idle.
3. Wait for session expiration.
4. Return to the app.
5. Perform an action.

I would verify that:

* User receives the appropriate message.
* Unauthorized requests are not executed.
* User is redirected to login when required.
* Unsaved information is handled correctly.
* Refreshing a token works when applicable.

---

## 30. How would you test application security from a QA perspective?

I would verify:

* Authentication
* Authorization
* Session management
* Secure communication
* Sensitive data handling
* Token expiration
* Password masking
* Secure storage
* Logout behavior
* Screenshot restrictions where required
* Input validation
* Error-message exposure

I would not attempt unauthorized exploitation unless security testing is explicitly approved.

---

## 31. How would you test sensitive data stored on the device?

I would verify whether sensitive information is stored in:

* Application databases
* Preferences
* Cache
* Logs
* Files
* Secure storage/keychain
* Temporary files

I would verify that sensitive information is not unnecessarily exposed in plain text.

---

## 32. How would you test application behavior with low device storage?

I would reduce available storage and test:

* Application launch
* File downloads
* Uploads
* Camera usage
* Cache creation
* Database operations
* Application upgrade

The application should fail gracefully and provide meaningful feedback.

---

## 33. How would you test battery consumption?

I would test the application under:

* Long-running foreground usage
* Background usage
* GPS usage
* Bluetooth usage
* Frequent API calls
* Push notifications
* Continuous synchronization

I would compare battery behavior against expected application usage patterns.

---

## 34. How would you test memory consumption?

I would perform repeated actions such as:

* Opening/closing screens
* Loading large datasets
* Uploading images
* Navigating repeatedly
* Switching foreground/background
* Running the app for an extended period

I would monitor memory usage and look for memory leaks or abnormal growth.

---

## 35. How would you test an application that uploads images?

I would test:

* Small image
* Large image
* Unsupported format
* Corrupted image
* Multiple images
* Camera image
* Gallery image
* Upload cancellation
* Network interruption
* Duplicate upload
* Upload timeout
* Insufficient storage

I would verify both UI behavior and backend data.

---

## 36. The upload succeeds but the image is missing from the backend. How would you investigate?

I would trace the complete flow:

**Mobile UI → API request → API response → backend service → database/storage**

I would verify:

* Request payload
* File metadata
* HTTP status code
* Response body
* Backend logs
* Storage location
* Database record

This helps identify whether the problem is in the mobile app, API, or backend.

---

## 37. How would you test mobile application performance?

I would measure:

* Application startup time
* Screen loading time
* API response time
* Scrolling performance
* Image loading
* Memory usage
* CPU usage
* Network usage
* Battery usage

I would test on different device capabilities and network conditions.

---

## 38. A screen takes 30 seconds to load. How would you determine whether it is a mobile or backend issue?

I would inspect:

1. UI action timestamp.
2. API request timestamp.
3. API response timestamp.
4. Backend processing time.
5. UI rendering time.

If the API itself takes 30 seconds, it is likely backend/API related.

If the API responds quickly but the screen takes 30 seconds to display, I would investigate the mobile application's processing/rendering.

---

## 39. How would you test an application with poor network connectivity?

I would test:

* 2G/slow network where applicable
* Weak Wi-Fi
* High latency
* Packet loss
* Network switching
* Intermittent connectivity
* Request timeout
* Response timeout

I would verify that the application provides useful feedback and does not create duplicate transactions.

---

## 40. How would you test application behavior when an API returns 500?

I would verify:

* Error message
* Retry behavior
* UI state
* Logging
* No duplicate transaction
* No application crash
* Recovery after backend becomes available

I would also verify whether the correct error is displayed to the user rather than exposing technical backend information.

---

## 41. What would you test for HTTP 401 and 403 responses?

### 401 Unauthorized

I would verify:

* Token expiration
* Login redirection
* Token refresh
* Session handling

### 403 Forbidden

I would verify:

* User permissions
* Role-based access
* Appropriate error handling
* Restricted functionality

---

## 42. How would you test an application after a backend API change?

I would perform:

* API contract validation
* Smoke testing
* Regression testing
* Authentication testing
* Data validation
* Negative testing
* Mobile UI validation

I would pay particular attention to fields added, removed, renamed, or changed in type.

---

## 43. How would you test backward compatibility?

I would test:

* Older app + current backend
* Current app + supported backend
* Old cached data + new application
* Existing sessions
* Existing users
* Existing records

I would identify whether API changes break older supported application versions.

---

## 44. How would you test mobile application accessibility?

I would verify:

* Screen reader support
* VoiceOver on iOS
* TalkBack on Android
* Accessibility labels
* Focus order
* Font scaling
* Color contrast
* Touch target size
* Keyboard navigation where applicable
* Dynamic text

Critical actions should remain usable with accessibility features enabled.

---

## 45. How would you test an application with a maximum text length?

I would test:

* Below maximum
* Exactly maximum
* Above maximum
* Empty input
* Spaces
* Unicode
* Emoji
* Copy/paste
* Very large pasted text

I would verify both UI restrictions and backend validation.

---

## 46. How would you test app behavior after a device reboot?

I would:

1. Log in.
2. Perform some application activity.
3. Restart the device.
4. Launch the application.

I would verify:

* Session behavior
* Stored data
* Notifications
* Background services
* Device permissions
* Application state
* Cached information

---

## 47. How would you test an application when the device date is changed manually?

I would test:

* Date moved forward
* Date moved backward
* Time changed
* Time zone changed
* Automatic date/time disabled

I would verify that business rules do not incorrectly rely on device time when server time should be authoritative.

---

## 48. How would you test multiple rapid taps on a Submit button?

I would tap the button repeatedly and verify:

* Only one request is created.
* Button becomes disabled where appropriate.
* Duplicate records are not created.
* UI remains stable.
* Backend handles duplicate requests safely.

This is especially important for payments, bookings, and other transactional operations.

---

## 49. A user presses Back during an important transaction. What would you test?

I would verify:

* Confirmation dialog if required
* Transaction cancellation
* Data preservation
* API request state
* Navigation
* Duplicate transaction prevention
* Recovery behavior

I would especially test this for payment, booking, registration, and submission workflows.

---

## 50. How would you test app behavior when the user kills the application during a transaction?

I would:

1. Start a transaction.
2. Submit the transaction.
3. Force close the application at different points.
4. Reopen the app.
5. Verify transaction status.

I would ensure that the backend does not create inconsistent or duplicate transactions.

---

## 51. How would you test application behavior after a forced close?

I would verify:

* Application launches successfully.
* Session behavior is correct.
* Data is preserved when expected.
* Pending transactions are handled safely.
* Cached data is consistent.
* Application does not crash again.

---

## 52. How would you test mobile app upgrade when database schema changes?

I would verify:

* Existing database migration
* New fields
* Removed fields
* Data preservation
* Default values
* Null handling
* Migration failure handling
* Rollback behavior where supported

I would test upgrades from multiple previous versions if those versions are officially supported.

---

## 53. How would you test an application across different screen sizes?

I would test:

* Small screens
* Standard screens
* Large screens
* Different resolutions
* Different aspect ratios
* Notched devices
* Foldable devices where supported

I would look for:

* Overlapping controls
* Clipped text
* Hidden buttons
* Incorrect spacing
* Broken scrolling
* Keyboard layout issues

---

## 54. How would you test a mobile application with Bluetooth connectivity?

I would test:

* Bluetooth enabled
* Bluetooth disabled
* Device pairing
* Incorrect device
* Pairing failure
* Connection loss
* Reconnection
* Multiple devices
* Application backgrounding
* Device restart

I would verify appropriate permission and error handling.

---

## 55. How would you test an application that communicates with a vehicle through Bluetooth?

I would test:

* Initial pairing
* Reconnection
* Vehicle unavailable
* Bluetooth disabled
* Vehicle ignition state
* Signal loss
* Multiple vehicles/devices
* App background/foreground
* Device reboot
* Network loss while Bluetooth remains available

I would validate both the mobile UI and underlying communication state.

---

## 56. How would you test app behavior when the device changes from one time zone to another?

I would verify:

* Scheduled events
* Appointment times
* Notifications
* Date displays
* Time displays
* API timestamps
* Daylight saving behavior

I would determine whether times are expected to display in device time, user time zone, or server/business time zone.

---

## 57. How would you test a mobile application after clearing cache?

I would verify:

* Application launch
* Login/session
* Stored preferences
* Cached data
* API calls
* Images/resources
* Application performance
* Data consistency

The application should rebuild required cache without corrupting user data.

---

## 58. How would you test logout functionality?

I would verify:

* User is logged out.
* Access token is invalidated/removed as expected.
* Protected screens cannot be accessed.
* Back navigation does not expose authenticated content.
* Sensitive cached data is handled correctly.
* Reopening the app does not unexpectedly log the user back in.

---

## 59. How would you test multi-user behavior on the same device?

I would:

1. Log in as User A.
2. Perform user-specific actions.
3. Log out.
4. Log in as User B.
5. Verify that User B cannot access User A's data.

I would pay particular attention to:

* Cache
* Local database
* Preferences
* Tokens
* Notifications
* Recently viewed information

---

## 60. How would you investigate a defect that occurs only on one specific device?

I would collect:

* Device model
* OS version
* App version
* Build number
* Screen resolution
* Available storage
* Network type
* Device settings
* Permissions
* Reproduction steps
* Logs

Then I would attempt reproduction on the same device/OS combination and compare with other devices.

---

## 61. How would you decide whether a mobile defect is high severity?

I would consider:

* Business impact
* Number of affected users
* Frequency
* Data loss
* Security impact
* Application crash
* Core functionality affected
* Workaround availability
* Release impact

For example, an application crash during login would normally be much more severe than a minor UI alignment issue.

---

## 62. A defect cannot be reproduced consistently. What would you do?

I would collect:

* Exact steps
* Device/OS
* App version
* Network condition
* Account information/test data
* Timestamp
* Logs
* Screen recording
* Frequency of occurrence

I would look for patterns such as specific devices, users, data, timing, or network conditions.

---

## 63. How would you test mobile application analytics events?

I would verify:

* Event triggered at the correct action.
* Correct event name.
* Correct parameters.
* Correct user/session identifiers.
* No duplicate events.
* Events are not triggered for failed actions.
* Events work across supported platforms.

I would compare application behavior with analytics/debug logs.

---

## 64. How would you test an application after changing the user's language?

I would verify the change across:

* Current screen
* Navigation
* Menus
* Buttons
* Error messages
* Notifications
* API content
* Date/time formatting
* Dynamic content

I would also restart the application and verify whether the language persists correctly.

---

## 65. How would you perform mobile regression testing before production release?

I would prioritize:

### Smoke Testing

* Installation
* Launch
* Login
* Core navigation
* Critical APIs
* Main business flow

### Functional Regression

* Major features
* Existing workflows
* New changes
* Defect fixes

### Compatibility

* Supported Android versions
* Supported iOS versions
* Critical devices

### Network

* Wi-Fi
* Cellular
* Offline
* Network switching

### Interruption

* Calls
* Notifications
* Background/foreground
* Device lock

### Release Validation

* App version
* Build number
* Environment
* Configuration
* Analytics
* Crash monitoring

---

## 66. Scenario: A production mobile application crashes for only 1% of users. How would you handle it?

I would first determine the affected population.

I would analyze:

* Device model
* OS version
* App version
* Geographic region
* Account type
* Network
* Feature being used
* Crash stack traces

I would identify common characteristics and prioritize reproduction based on the highest-impact combination.

---

## 67. Scenario: The developer says, "It works on my device." How would you respond?

I would avoid treating one successful device as proof that the application is correct.

I would provide:

* Exact reproduction steps
* Device model
* OS version
* App version/build
* Expected result
* Actual result
* Logs
* Screenshots/video
* Network information
* Test data

I would demonstrate the issue on the affected configuration whenever possible.

---

## 68. Scenario: A mobile app works in the development environment but fails in production. What would you investigate?

I would compare:

* API endpoints
* Environment configuration
* Authentication
* Certificates
* Feature flags
* Database data
* Backend versions
* Network configuration
* Push notification configuration
* Third-party integrations

I would confirm whether the problem is application code or production configuration.

---

## 69. Scenario: The application displays stale information after a backend update. How would you investigate?

I would determine whether stale data comes from:

* Local cache
* Application database
* API cache
* Backend cache
* CDN
* Delayed synchronization

I would compare the mobile API response with the backend/database source of truth.

---

## 70. Scenario: A booking is created twice when the user taps Submit twice. How would you handle it?

I would classify this as a potentially serious transactional defect.

I would test:

* Rapid double tap
* Slow repeated tap
* Network latency
* Timeout followed by retry
* App backgrounding during submission
* Reopening the app

I would recommend preventing duplicate UI submissions and ensuring backend idempotency where appropriate.

---

## 71. Scenario: The app shows "Success" but the backend transaction failed. How would you investigate?

I would trace:

**User Action → Mobile Request → API Response → Backend Processing → Database**

I would compare the success condition used by the mobile app against the actual API response and backend transaction status.

This could indicate incorrect client-side response handling or an API contract issue.

---

## 72. Scenario: A customer reports that the app is extremely slow only during peak hours. What would you check?

I would compare:

* Peak vs non-peak response times
* API latency
* Backend CPU/memory
* Database performance
* Network latency
* Concurrent users
* Request volume
* Application rendering

I would determine whether the bottleneck is client-side, network-related, or backend infrastructure-related.

---

## 73. Scenario: A new app version is released, and users report that they are unexpectedly logged out. What would you investigate?

I would check:

* Token format
* Token storage
* Authentication API changes
* Secure storage migration
* Database migration
* Session expiration
* Encryption/key changes
* App upgrade logic

I would reproduce using an existing authenticated account and upgrade from the previous production version.

---

## 74. Scenario: A user receives a notification for another user's account. What would you do?

I would treat this as a **critical security/privacy defect**.

I would immediately:

1. Capture evidence.
2. Stop unnecessary further testing with real user data.
3. Notify the appropriate security/product/development teams.
4. Identify the scope.
5. Verify notification-token/account mapping.
6. Validate backend authorization and notification targeting.

I would avoid exposing or sharing real customer information in defect reports.

---

## 75. What is your overall approach to mobile application testing?

My approach is:

1. Understand business requirements.
2. Identify supported platforms and devices.
3. Review APIs and backend dependencies.
4. Prepare test data.
5. Perform installation and smoke testing.
6. Execute functional testing.
7. Validate API/UI/data integration.
8. Test network conditions.
9. Test interruptions and lifecycle events.
10. Test compatibility.
11. Test localization.
12. Test accessibility.
13. Test security-sensitive behavior.
14. Perform regression testing.
15. Validate crash/performance behavior.
16. Report defects with complete evidence.
17. Perform production sanity testing.
18. Monitor post-release issues.

The key principle is to test not only the application's happy path, but also **real-world mobile conditions** such as network changes, device differences, interruptions, permissions, background execution, upgrades, and limited device resources.

---

# Quick Mobile QA Interview Checklist

* Installation and uninstallation
* Upgrade testing
* Android testing
* iOS testing
* Device compatibility
* OS compatibility
* Network testing
* Offline testing
* Wi-Fi/mobile-data switching
* Airplane mode
* Application lifecycle
* Background/foreground
* Device lock/unlock
* Incoming calls
* Notifications
* Push notifications
* Deep links
* Permissions
* Location
* Bluetooth
* Camera
* Microphone
* Biometric authentication
* Session management
* Logout
* Localization
* Date/time/time zones
* Accessibility
* Performance
* Memory
* Battery
* Storage
* Crash testing
* API integration
* Data validation
* Security validation
* Analytics validation
* App upgrade
* Database migration
* Multi-user testing
* Device reboot
* Cache behavior
* Production validation
* Real-world scenario testing

# Senior-Level Interview Tip

When answering mobile testing scenario questions, structure the answer around:

**Understand → Reproduce → Isolate → Collect Evidence → Validate Client/API/Backend → Assess Impact → Report → Retest → Regression**

For example:

> "First I would reproduce the issue and capture the exact device, OS, app build, network condition, and test data. Then I would isolate whether the issue is in the mobile UI, API, network, or backend by tracing the request and response. I would collect logs and screenshots/video, assess severity and business impact, report the defect with complete evidence, verify the fix, and perform targeted regression across the affected device and OS combinations."

This approach demonstrates **real-world senior QA troubleshooting rather than simply listing test cases**.
