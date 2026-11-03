# AgentHub Admin Panel Specification

## Product Description

AgentHub is a startup building a SaaS platform where companies rent pre-configured AI agents and deploy them for specific business tasks. Agents can be equipped with skills such as web browsing, document reading, and calendar management. The admin panel is for AgentHub operations administrators who oversee customers, agents, the skill catalog, rental contracts, revenue, and execution errors.

## Technology and Constraints

- Use semantic HTML for the page structure and Tailwind CSS loaded through its CDN for styling, including Tailwind's `dark:` utilities.
- Use vanilla JavaScript for navigation, menus, modals, collapsible content, theme switching, and other interactions. Do not use JavaScript frameworks or component libraries.
- Build a front-end-only prototype with hardcoded sample data. Do not add a backend, API calls, authentication, or persistent data storage.
- Use a responsive admin layout: persistent sidebar navigation on desktop and a compact, usable navigation treatment on narrow screens. Keep tables readable on mobile by allowing horizontal scrolling or using an equivalent compact layout.
- Provide clear focus states and keyboard-operable controls. Use text labels alongside status colors so color is not the only signal.

## Global Shell and Navigation

1. **Sidebar navigation:** Show AgentHub branding and links to Dashboard, User Management, Agent Management, Skills, Agent Contracts, and Error Log. Keep the sidebar visible while navigating between sections, indicate the current section, and make each link switch the main content without a page reload.
2. **Top bar:** Display the current section title and a dark mode toggle on every section. The toggle changes the whole interface between light and dark themes using Tailwind `dark:` utilities.
3. **Content area:** Use consistent page padding, readable headings, and restrained borders, spacing, and shadows. At narrow viewport widths, the content must fit the screen without controls overlapping; wide tables may scroll horizontally.

## 1. Dashboard

1. **Metric cards:** Display four cards for revenue generated this month, discount and coupon losses, active agents across all clients, and agents currently failing. Each card includes an identifying icon, label, hardcoded formatted value, and a distinct accent treatment; arrange them in a responsive two-column grid that becomes one column on small screens.
2. **Weekly activity placeholder:** Place a full-width chart placeholder below the metrics. Give it a dashed border, a centered “Weekly activity” label, and a fixed minimum height so it remains visibly distinct without requiring chart data or a charting library.
3. **Metric emphasis:** Use clear typography to distinguish each value from its label, with subtle card shadows and sufficient contrast in both themes. The failing-agent card must also make its alert state apparent without relying on color alone.

## 2. User Management

1. **Users table:** Show hardcoded registered users in a table with name, email, plan, status, and actions columns. Use a status badge for each user's status and preserve a readable layout on narrow screens.
2. **Row action dropdown:** Each row has a clearly labeled action button. Activating it opens a small menu with “View detail” and “Delete”; only the active row's menu is open, and selecting an action closes the menu.
3. **User detail modal:** “View detail” opens a centered modal overlay containing the selected user's full hardcoded record, including the table fields and any additional record details. Close it with a visible close button or by clicking the backdrop; clicks inside the dialog must not close it.

## 3. Agent Management

1. **Agents listing:** Show each hardcoded agent's name, owner, current status (active, inactive, or failing), skills summary, and actions. Use text-and-color status badges and include examples of all three statuses.
2. **Collapsible skill list:** Each agent has an expand/collapse control. Skill names are hidden by default; activating the control reveals that agent's complete skill list with a smooth height/opacity transition and updates the control's accessible expanded state.
3. **Agent action dropdown and configuration modal:** Each agent has an action menu with “Configure” and “Delete”. “Configure” opens a modal showing the selected agent's system prompt in a readable, preformatted text area; the modal can be closed with its close button or the backdrop.

## 4. Skills

1. **Section explanation:** Begin the section with a short in-panel explanation that a skill is a capability that can be attached to an AI agent, such as browsing the web, reading documents, or managing calendars.
2. **Skills catalog:** Display hardcoded skills as a compact table or list with skill name, short description, and the number of agents that currently have the skill enabled. Keep the count visually scannable.
3. **Skill actions:** Each skill has an action dropdown with “View detail” and “Delete”. “View detail” opens a modal containing the selected skill's name, full description, enabled-agent count, and any relevant sample metadata; the modal follows the shared close-button and backdrop behavior.

## 5. Agent Contracts

1. **Contracts table:** List hardcoded active and past rental contracts with client, rented agent, contracted skills, contract dates, total amount paid, contract status, and actions. Include both active and past examples.
2. **Contracted skills cell:** Summarize the contracted skills in each row without obscuring dates or payment amounts; show all skill names in the detail view. On mobile, keep the full record accessible through horizontal scrolling or a compact responsive layout.
3. **Contract detail modal:** The row's “View detail” action opens a modal with the full contract breakdown, including client and agent, contract dates and status, total paid, and an itemized list of contracted skills with each skill's individual price.

## 6. Error Log

1. **Error entries:** Show hardcoded agent execution errors with timestamp, agent name, error type, short description, and actions. Include multiple severity/type examples so the categorization is visible.
2. **Severity badges:** Use color-coded badges for error type or severity, with a readable text label in every badge. Keep badge colors and text legible in both light and dark themes.
3. **Error actions and detail modal:** Each entry has an action dropdown with “View detail” and “Mark as resolved”. “View detail” opens a modal with the full error trace and record details. “Mark as resolved” updates the entry's visible status and removes or disables the unresolved action for that entry.

## Reusable Component Inventory

- **Sidebar navigation:** Persistent section links and current-section state.
- **Metric card:** Icon, label, formatted value, and metric-specific accent.
- **Action dropdown:** Per-record trigger and contextual menu options; closes after an action or outside click.
- **Modal dialog:** Overlay, backdrop, close button, and content area shared by record detail and configuration views.
- **Badge:** Labeled status and severity treatment with theme-aware contrast.
- **Collapsible skill list:** Per-agent expand control and animated skill content.
- **Dark mode toggle:** Top-bar theme control that changes the entire interface.

## Acceptance Criteria

1. The sidebar displays all six sections, remains available while sections are changed, and visibly marks the current section.
2. The Dashboard shows all four required metric cards with hardcoded values and the weekly activity placeholder beneath them.
3. The four metric cards reflow from two columns to one column at a narrow viewport without clipping their labels or values.
4. Every User Management row has a dropdown that opens on activation, shows “View detail” and “Delete”, and closes after an option is selected or the user clicks outside it.
5. User “View detail” opens the selected user's record in a modal; the close button and backdrop close it, while clicking inside the modal does not.
6. Every agent's skill list starts collapsed; its control reveals and hides the complete list, transitions smoothly, and reports its expanded state accessibly.
7. Agent “Configure” opens a modal displaying that agent's system prompt, and the modal can be dismissed using its close button and backdrop.
8. The Skills section explains the meaning of a skill and displays each skill's description and enabled-agent count; skill actions include “View detail” and “Delete”.
9. Contract detail opens a modal showing the full contract record and an itemized skill list with individual prices.
10. Error entries use labeled, color-coded severity/type badges; “View detail” exposes the full trace and “Mark as resolved” visibly updates the selected entry.
11. The dark mode toggle switches every section between readable light and dark appearances using Tailwind `dark:` styling, and toggling back restores light mode.
12. All displayed data is hardcoded; the prototype runs without API requests, backend services, frameworks, or a charting library.
13. Dropdowns, modals, navigation links, theme toggle, and collapsible controls can be operated with a keyboard and show visible focus states.
