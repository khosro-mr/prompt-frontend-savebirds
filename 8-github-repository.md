<h1 align="center">SaveBirds.app GitHub Repository Page</h1>

# 1. Overview
Create the GitHub Repository page for SaveBirds.app using Vue 3 and Bootstrap 5. This page provides information about the SaveBirds.app GitHub organization, repository details, and contact information for collaboration or contributions.

# 2. Design Requirements

## 2.1. Layout Structure
The GitHub Repository page should consist of the following sections:
- **Title Section**: Page heading and introduction
- **Repository Information**: Details about the SaveBirds.app repository
- **GitHub Organization Details**: Information about the organization behind the project
- **README.md Content**: Display of the repository's README content
- **Contact Information**: Ways to reach out to the project maintainers

## 2.2. Visual Reference
![GitHub Repository Page Design](images/7-Github.png)

# 3. Component Specifications

## 3.1. Title Section
- **Title**:
  - Text: "GitHub"
  - Font: Large, bold, centered (display-4 or similar class)
  - Position: Top of the content area
  - Styling: Clean, professional appearance with appropriate spacing

- **Introduction Text**:
  - Content: Brief explanation of the open-source nature of SaveBirds.app
  - Length: 1-2 paragraphs
  - Position: Below the title
  - Style: Clean, readable font with appropriate line spacing

## 3.2. Repository Information
- **Repository Card**:
  - Style: GitHub-like card with light background and subtle border
  - Content: SaveBirds.app logo, repository name, and description
  - URL Display: Repository URL displayed prominently
  - Links: All blue text should be clickable and navigate to https://github.com/SaveBirds-app

- **Repository Details**:
  - Description: Concise explanation of the repository's purpose
  - Repository Statistics: Stars, forks, watchers (if available)
  - Last Updated: Information about the latest commit/update
  - License: Information about the project's license

## 3.3. GitHub Organization Section
- **Organization Card**:
  - Style: Similar to the repository card
  - Content: Organization name, description, and member information
  - Links: All blue text related to the organization should navigate to https://github.com/SaveBirds-app

- **People Section**:
  - Display: Profile images of organization members
  - Layout: Horizontal row of circular profile photos
  - Hover Effect: Show username on hover
  - Link: Each profile image should link to the respective GitHub profile

- **Tags/Topics**:
  - Display: List of clickable topic tags related to the project
  - Style: GitHub-style topic tags with light background
  - Behavior: Tags should be clickable and redirect to related GitHub topics

## 3.4. README.md Content
- **README Display**:
  - Content: Render the repository's README.md content
  - Styling: GitHub-like markdown styling
  - Layout: Full width of the content area with appropriate padding
  - Code Blocks: Properly formatted and syntax highlighted

## 3.5. Contact Information
- **Contact Card**:
  - Style: Clean card with contact details
  - Content: Email, LinkedIn, and personal website links

- **Contact Details**:
  - Email: mostafa.mohammadrezaee@gmail.com
  - LinkedIn: Link to Mostafa M. Rezaee's profile
  - Personal Website: Link to additional contact options

- **Organization Manager**:
  - Text: Information about the organization manager
  - Name: Mostafa M. Rezaee
  - Position: Organization manager/maintainer

# 4. Interactive Elements

## 4.1. Follow Button
- **Style**: GitHub-like "Follow" button
- **Action**: When clicked, should direct to follow the repository on GitHub
- **Visual**: Proper hover/active states

## 4.2. Repository Links
- **Style**: Blue text links
- **Action**: All blue text should be clickable and navigate to the appropriate GitHub pages
- **Target**: Links should open in a new tab

## 4.3. Embedded Content
- **GitHub README**: Properly rendered markdown content from the repository's README
- **Code Snippets**: Any code snippets should be properly formatted and syntax highlighted

# 5. Responsive Behavior
- **Desktop View**:
  - Full-width content layout with appropriate margins
  - Readable text size and spacing
  - Properly aligned cards and sections

- **Medium Screen View**:
  - Adjusted spacing and layout
  - Maintained readability of GitHub content
  - Properly scaled profile images in people section

- **Mobile View**:
  - Single-column, stacked layout
  - Full-width cards with appropriate padding
  - Properly sized text and interactive elements for touch input
  - Preserved GitHub styling in a mobile-friendly format

# 6. Implementation Notes
- Create as a Vue component in `views/GithubRepositoryView.vue`
- Use Bootstrap 5 for layout and styling
- Consider using a markdown parser library (such as marked.js) for rendering README content
- Implement external links with proper security attributes (rel="noopener noreferrer")
- Mimic GitHub's styling for tags, buttons, and cards
- Since this is a frontend-only implementation without actual GitHub API integration, use static content that resembles the GitHub interface

# 7. Component Data Structure
```javascript
data() {
  return {
    repositoryUrl: "https://github.com/SaveBirds-app",
    organizationName: "SaveBirds-app",
    repositoryDescription: "A web tool for analyzing the North American Breeding Bird Survey data to enhance conservation in protected areas",
    organizationMembers: [
      {
        id: 1,
        name: "Mostafa M. Rezaee",
        username: "mostafa-rezaee",
        avatar: "images/team/mostafa-rezaee.jpg",
        profileUrl: "https://github.com/mostafa-rezaee"
      },
      // Additional members...
    ],
    topics: ["conservation", "bird-survey", "data-analysis", "web-tool", "research"],
    contactInfo: {
      email: "mostafa.mohammadrezaee@gmail.com",
      linkedin: "https://www.linkedin.com/in/mostafa-m-rezaee/",
      website: "https://mostafa-mr.com/"
    },
    readmeContent: `
      # SaveBirds.app

      A web tool for analyzing the North American Breeding Bird Survey data to enhance conservation in protected areas.

      ## Features

      - Metrics analysis
      - Presence-Absence data visualization
      - Bird Atlas Generator
      - And more...

      ## Getting Started

      ...
    `
  }
}
```

# 8. Code Structure
- Use semantic HTML5 elements (`<section>`, `<article>`, etc.)
- Implement as a single-file component with template, script, and style sections
- Style using Bootstrap classes with GitHub-inspired custom CSS
- For any custom styles, use scoped CSS to avoid conflicts
- Structure the component with clearly defined sections
- Include appropriate comments for complex logic
