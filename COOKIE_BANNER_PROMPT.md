# GDPR-Compliant Cookie Banner Implementation Prompt

Use this prompt to add a consistent GDPR-compliant cookie banner to web projects:

---

Add a GDPR-compliant cookie notification banner with the following requirements:

## Functionality Requirements:
1. Display a fixed banner at the bottom of the page on first visit only
2. Provide two clear options: "Accept" and "Decline"
3. Store user's choice in localStorage to persist across sessions
4. Show the banner 500ms after page load for better UX
5. Hide the banner immediately after user makes a choice
6. Conditionally initialize analytics/tracking tools ONLY if user accepts cookies
7. Never show the banner again once user has made a choice

## Technical Implementation:
1. **Analytics Integration**: Wrap all analytics initialization (Datadog RUM, Google Analytics, etc.) in a function that only executes if cookies are accepted
2. **LocalStorage Key**: Use 'cookieConsent' with values 'accepted' or 'declined'
3. **Check on Load**: Check localStorage on page load - if consent exists and equals 'accepted', initialize analytics immediately
4. **Smooth Animation**: Include a slide-up animation when banner appears

## Design Requirements:
1. **Position**: Fixed to bottom of viewport, full width
2. **Style**: Dark background (#1a202c), white text, high contrast
3. **Layout**: Flexbox layout with text on left, buttons on right
4. **Buttons**:
   - Accept: Green background (#48bb78), prominent
   - Decline: Transparent with white border, secondary style
   - Both buttons: Rounded (25px), padding, hover effects
5. **Mobile Responsive**: Stack vertically on mobile, full-width buttons
6. **Accessibility**: Include ARIA labels, role="dialog", keyboard navigation support
7. **Z-index**: High value (9999) to ensure visibility above other content

## Content Requirements:
1. **Clear Heading**: "We Value Your Privacy" or similar
2. **Explanation**: Brief description of what cookies/analytics are used for
3. **Link**: Include link to privacy policy or GDPR compliance documentation
4. **Transparency**: Mention specific tools being used (e.g., "Datadog RUM", "Google Analytics")

## Example Message:
"This website uses cookies and analytics to improve your experience and measure performance metrics. By clicking 'Accept', you consent to our use of cookies and analytics tools like [Tool Name]. [Learn more]"

## Key Code Structure:
```javascript
// 1. Wrap analytics initialization
function initializeAnalytics() {
    // Your analytics code here
}

// 2. Check consent on load
const cookieConsent = localStorage.getItem('cookieConsent');
if (cookieConsent === 'accepted') {
    initializeAnalytics();
}

// 3. Handle accept
function acceptCookies() {
    localStorage.setItem('cookieConsent', 'accepted');
    hideBanner();
    initializeAnalytics();
}

// 4. Handle decline
function declineCookies() {
    localStorage.setItem('cookieConsent', 'declined');
    hideBanner();
}

// 5. Show banner if no choice made
if (!cookieConsent) {
    setTimeout(showBanner, 500);
}
```

## Testing Checklist:
- [ ] Banner appears on first visit after 500ms
- [ ] Banner does not appear on subsequent visits after accepting
- [ ] Banner does not appear on subsequent visits after declining
- [ ] Analytics initialize immediately on page load for users who previously accepted
- [ ] Analytics do NOT initialize for users who declined
- [ ] Accept button properly initializes analytics
- [ ] Decline button does not initialize analytics
- [ ] Banner is responsive on mobile devices
- [ ] All buttons are keyboard accessible
- [ ] Banner has proper ARIA labels for screen readers
- [ ] User can clear localStorage to test banner reappearance

---

**Usage**: Copy this prompt and paste it into any project where you need to add GDPR-compliant cookie consent. Adjust the analytics tool names and styling colors to match your project's branding.