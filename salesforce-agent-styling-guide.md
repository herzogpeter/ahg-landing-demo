# Salesforce Agentforce Chat Widget Styling Guide

## Overview
This guide provides step-by-step instructions to customize the Salesforce Agentforce chat widget to match American Hartford Gold's brand colors and styling.

## Brand Colors Reference
- **Primary Navy:** `#1e3a5f`
- **Gold:** `#FFD700` 
- **Red:** `#dc3545`
- **White:** `#FFFFFF`

---

## Method 1: Salesforce Setup Configuration (Recommended)

### Step 1: Access Digital Experiences
1. Log into Salesforce
2. Navigate to **Setup** (gear icon in top right)
3. In Quick Find box, type "Digital Experiences"
4. Click **All Sites**
5. Find your site: **ESWWebInquiries**
6. Click **Builder** or **Workspaces**

### Step 2: Access Embedded Service Configuration
1. In the site workspace, go to **Administration**
2. Look for **Messaging Settings** or **Embedded Service Deployments**
3. Click on your deployment: **Web_Inquiries**

### Step 3: Customize Appearance
1. Find the **Appearance** or **Branding** tab
2. Configure these settings:

   **Primary Elements:**
   - **Header Background Color:** `#1e3a5f`
   - **Header Text Color:** `#FFFFFF`
   - **Primary Button Color:** `#FFD700`
   - **Primary Button Text:** `#1e3a5f`
   
   **Chat Elements:**
   - **Agent Message Background:** `#f5f5f5`
   - **Customer Message Background:** `#1e3a5f`
   - **Customer Message Text:** `#FFFFFF`
   - **Chat Background:** `#FFFFFF`
   
   **Widget Button:**
   - **Button Background:** `#FFD700`
   - **Button Icon Color:** `#1e3a5f`
   - **Button Hover Color:** `#FFA500`

4. Upload a logo (optional):
   - Click **Upload Logo**
   - Use a transparent PNG of the AHG lion logo
   - Recommended size: 40x40px

5. **Save** your changes
6. **Publish** the site

---

## Method 2: Code-Based Configuration

### Step 1: Update Your HTML Embed Code
Add styling settings to your `initEmbeddedMessaging()` function:

```javascript
function initEmbeddedMessaging() {
    try {
        // Add custom styling
        embeddedservice_bootstrap.settings.language = 'en_US';
        
        // Color customizations
        embeddedservice_bootstrap.settings.primaryColor = '#1e3a5f';
        embeddedservice_bootstrap.settings.secondaryColor = '#FFD700';
        embeddedservice_bootstrap.settings.backgroundPrimary = '#FFFFFF';
        embeddedservice_bootstrap.settings.backgroundSecondary = '#f5f5f5';
        
        // Font customization
        embeddedservice_bootstrap.settings.font = 'Helvetica Neue, Arial, sans-serif';
        embeddedservice_bootstrap.settings.fontSize = '14px';
        
        // Widget positioning (optional)
        embeddedservice_bootstrap.settings.widgetWidth = '350px';
        embeddedservice_bootstrap.settings.widgetHeight = '500px';
        
        // Initialize with existing settings
        embeddedservice_bootstrap.init(
            '00DgL000004Ss9d',
            'Web_Inquiries',
            'https://orgfarm-b50a197801-dev-ed.develop.my.site.com/ESWWebInquiries1754683767882',
            {
                scrt2URL: 'https://orgfarm-b50a197801-dev-ed.develop.my.salesforce-scrt.com'
            }
        );
    } catch (err) {
        console.error('Error loading Embedded Messaging: ', err);
    }
}
```

---

## Method 3: Custom CSS Override

### Step 1: Add Custom CSS to Your Page
Add this CSS to your HTML file to override default styles:

```css
<style>
/* Chat widget button */
.embeddedMessagingFrame {
    bottom: 20px !important;
    right: 20px !important;
}

.embeddedMessagingIconButton {
    background-color: #FFD700 !important;
    box-shadow: 0 4px 12px rgba(255, 215, 0, 0.4) !important;
}

.embeddedMessagingIconButton:hover {
    background-color: #FFA500 !important;
    transform: scale(1.05) !important;
}

/* Chat window header */
.embeddedMessagingHeader {
    background: linear-gradient(135deg, #1e3a5f 0%, #2c4d7a 100%) !important;
}

.embeddedMessagingHeaderText {
    color: #FFFFFF !important;
}

/* Chat messages */
.embeddedMessagingAgentMessage {
    background-color: #f5f5f5 !important;
    color: #333333 !important;
}

.embeddedMessagingCustomerMessage {
    background-color: #1e3a5f !important;
    color: #FFFFFF !important;
}

/* Input area */
.embeddedMessagingTextAreaWrapper {
    border-top: 2px solid #FFD700 !important;
}

.embeddedMessagingSendButton {
    background-color: #FFD700 !important;
    color: #1e3a5f !important;
}

.embeddedMessagingSendButton:hover {
    background-color: #FFA500 !important;
}

/* Minimize/close buttons */
.embeddedMessagingMinimizeButton,
.embeddedMessagingCloseButton {
    color: #FFD700 !important;
}
</style>
```

### Step 2: Place CSS Before the Salesforce Script
Ensure the custom CSS is placed in the `<head>` section of your HTML file, before the Salesforce embed script loads.

---

## Method 4: Experience Cloud Site Builder (Visual Editor)

### Step 1: Access Experience Builder
1. Go to **Digital Experiences** → **All Sites**
2. Click **Builder** next to your site
3. This opens the visual Experience Builder

### Step 2: Theme Settings
1. Click the **paintbrush icon** (Themes) in the left sidebar
2. Select **Theme Settings** or **Colors & Branding**
3. Update the color palette:
   - Primary Action: `#FFD700`
   - Brand Color: `#1e3a5f`
   - Success: `#28a745`
   - Error: `#dc3545`

### Step 3: Component-Specific Styling
1. Click on the **Embedded Service Chat** component
2. In the properties panel, look for:
   - Background Color
   - Text Color
   - Button Style
   - Border Radius
3. Update each to match brand guidelines

### Step 4: Preview and Publish
1. Click **Preview** to test the changes
2. Test on desktop and mobile views
3. Click **Publish** when satisfied

---

## Testing Your Changes

### Local Testing
1. Clear your browser cache
2. Open Chrome DevTools (F12)
3. Go to **Application** → **Clear Storage** → **Clear site data**
4. Reload: `http://localhost:8000/ahg-accurate.html`
5. Check if styling is applied

### Debugging Tips
- Open browser console to check for errors
- Use DevTools Elements panel to inspect widget classes
- Look for CSS conflicts with `!important` declarations
- Verify Salesforce configuration is published

---

## Troubleshooting

### Changes Not Appearing?
1. **Cache Issues:**
   - Hard refresh: `Ctrl+Shift+R` (Windows) or `Cmd+Shift+R` (Mac)
   - Try incognito/private browsing mode

2. **Salesforce Deployment:**
   - Ensure changes are **Published** not just saved
   - Wait 5-10 minutes for changes to propagate
   - Check deployment status in Salesforce

3. **CSS Specificity:**
   - Add `!important` to override stubborn styles
   - Use more specific selectors
   - Check for iframe restrictions

### Widget Not Loading?
- Verify you're using `http://localhost:8000` not `file://`
- Check Salesforce site is activated
- Confirm CORS settings include `http://localhost:8000`

---

## Additional Resources

- [Salesforce Embedded Service Documentation](https://help.salesforce.com/s/articleView?id=sf.embedded_service_setup.htm)
- [Experience Cloud Styling Guide](https://help.salesforce.com/s/articleView?id=sf.community_builder_theme.htm)
- [Web Chat Branding Best Practices](https://help.salesforce.com/s/articleView?id=sf.embedded_chat_branding.htm)

---

## Notes
- Some styling options may require specific Salesforce licenses or permissions
- Complex customizations might need Salesforce administrator access
- Test all changes in a sandbox environment first if available