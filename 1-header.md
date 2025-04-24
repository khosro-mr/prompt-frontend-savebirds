<h1 align="center">SaveBirds.app Header/Navigation Bar</h1>

# 1. Overview
Create a responsive header/navigation bar component for SaveBirds.app using Vue 3 and Bootstrap 5. This component should appear on all pages and provide navigation to all major sections of the site.

# 2. Design Requirements

## 2.1. Layout Structure
The header should be divided into three distinct sections:
- **Left Section**: Logo and site name
- **Center Section**: Main navigation menu items
- **Right Section**: "Get Started" action button

## 2.2. Visual Reference
![Header Design](images/header.png)

# 3. Component Specifications

## 3.1. Left Section
- **Logo**: 
  - Image source: `images/logo.png`
  - Size: Appropriate size that maintains proportions (approx. height of 40px)
  - Alt text: "SaveBirds Logo"
  
- **Site Name**:
  - Text: "SaveBirds"
  - Font: Bold, same font family as the rest of the site
  - Positioned directly to the right of the logo
  - Should be clickable and link to the home page

## 3.2. Center Section
- **Menu Items**:
  - Display horizontally with appropriate spacing
  - Each item should be clickable and navigate to the corresponding section
  - Active menu item should be visually distinct (underlined or highlighted)
  - Menu items (in order):
    1. Home
    2. Metrics
    3. Presence-Absence Data
    4. Bird Atlas Generator
    5. Our Team
    6. Ongoing Projects

## 3.3. Right Section
- **Action Button**:
  - Text: "Get Started"
  - Color: Green (#28a745 or Bootstrap's .btn-success)
  - Hover effect: Slightly darker shade of green
  - Action: When clicked, navigate to the Metrics page
  - Visual: Rounded corners, appropriate padding

# 4. Responsive Behavior
- On desktop: Display all elements as described above
- On smaller screens: Consider implementing a hamburger menu for the navigation items
- Ensure the logo and site name remain visible at all viewport sizes

# 5. Implementation Notes
- Create as a reusable Vue component in `components/layout/AppHeader.vue`
- Use Vue Router for navigation links (`router-link` component)
- Implement with Bootstrap 5 classes for styling and responsiveness
- Ensure accessibility with proper aria attributes and keyboard navigation
- All navigation links should use anchor tags with proper IDs for smooth scrolling

# 6. Code Structure
- Use semantic HTML5 elements (`<header>`, `<nav>`, etc.)
- Implement as a single-file component with template, script, and style sections
- Style using Bootstrap classes with minimal custom CSS
- For any custom styles, use scoped CSS to avoid conflicts
