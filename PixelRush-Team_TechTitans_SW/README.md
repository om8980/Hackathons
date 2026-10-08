# Blood Relay

Blood Relay is a static front-end prototype for coordinating blood donation requests in India. It presents the requester and donor journeys across a set of linked HTML pages, styled with plain CSS.

> **Prototype only:** The pages show sample profiles and demo flows. There is no backend, authentication, persistent data store, or real donor matching/notification service. Do not use this prototype to request or coordinate real medical care.

## Features

- Landing page describing the service and linking to key actions.
- Donor registration, search, profile, and dashboard screens.
- Blood request and emergency request screens.
- Matching, donor confirmation, tracking, and request status screens.
- Notifications and profile preference screens.
- Responsive layouts implemented with HTML and CSS.

## Run locally

No build tools or dependencies are required.

1. Clone or download this repository.
2. Open `index.html` in a browser, or serve the project directory with any static HTTP server.

For example, if Python is installed:

```bash
python -m http.server 8000
```

Then visit [http://localhost:8000](http://localhost:8000).

## Project structure

- `index.html`, `about.html`, `search.html`, `request.html`, etc. — individual screens and flows.
- Matching `.css` files — page-specific styles. `styles.css` contains shared styling used by parts of the prototype.
- `blood logo.png` and `ChatGPT Image Oct 6, 2026, 01_13_18 AM.png` — image assets.

Navigation between screens uses ordinary links, so pages can also be opened directly. Some profile imagery is loaded from Unsplash and needs an internet connection.

## Technology

- HTML5
- CSS3
- No JavaScript framework, package manager, or build step

## Contributing

Keep new screens consistent with the existing page and stylesheet structure. Since this is currently a visual prototype, integrations such as real donor data, authentication, request persistence, and notifications would require a backend and appropriate privacy and security design.
