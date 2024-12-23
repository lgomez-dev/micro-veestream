# TODOs for Streaming Platform Project

## Project Setup
- [ ] Initialize a Git repository for version control.
- [ ] Set up a mono-repo or separate repos for frontend and backend.
- [ ] Write a detailed README.md to document the project.

## Frontend (Svelte)
### Setup
- [ ] Create a Svelte project using `npx degit sveltejs/template`.
- [ ] Install dependencies:
  - [ ] `video.js` for video playback.
  - [ ] `axios` for API calls.
- [ ] Configure environment variables for API URLs.

### Components
- [ ] **Header Component**:
  - [ ] Include navigation for Home, Browse, and Profile.
- [ ] **Video Player Component**:
  - [ ] Integrate Video.js for video playback.
  - [ ] Add functionality to handle HLS/DASH formats.
  - [ ] Save playback progress locally and/or via API.
- [ ] **Login and Signup Forms**:
  - [ ] Create forms for user authentication.
  - [ ] Handle form submission and API integration.
- [ ] **Browse Page**:
  - [ ] Fetch and display a list of videos.
  - [ ] Include search functionality using Solr APIs.
  - [ ] Implement pagination or infinite scrolling.
- [ ] **Profile Page**:
  - [ ] Display user details.
  - [ ] Show watched history or saved videos (if applicable).

### Styling
- [ ] Use a CSS framework like TailwindCSS or write custom styles.
- [ ] Ensure responsive design for mobile and desktop.

---

## Backend (Golang)
### Setup
- [ ] Initialize a Go project with `go mod init`.
- [ ] Install required packages:
  - [ ] `gorilla/mux` for routing.
  - [ ] `gorm` for PostgreSQL ORM.
  - [ ] `mongo-driver` for MongoDB.
  - [ ] `net/http` for building HTTP APIs.

### Database Integration
#### PostgreSQL
- [ ] Set up a database for user authentication and relational data.
- [ ] Create tables:
  - [ ] `users` (id, username, email, password hash).
  - [ ] `subscriptions` (user_id, status, etc.).
  - [ ] `video_progress` (user_id, video_id, progress).

#### MongoDB
- [ ] Configure MongoDB for video metadata storage.
- [ ] Define collections:
  - [ ] `videos` (id, title, description, tags, cloudflare_url, etc.).

#### Apache Solr
- [ ] Install and configure Apache Solr.
- [ ] Define schemas for indexing video metadata.
- [ ] Write scripts to populate Solr with video data.

### API Development
- [ ] **Authentication APIs**:
  - [ ] `/signup` for new users.
  - [ ] `/login` to authenticate users.
  - [ ] Use JWT for session management.
- [ ] **Video APIs**:
  - [ ] `/videos` to fetch a list of videos.
  - [ ] `/video/{id}` to fetch specific video details.
  - [ ] `/stream/{video-id}` to generate a secure video playback URL.
- [ ] **Search APIs**:
  - [ ] `/search?q={query}` to fetch results from Solr.
- [ ] **Progress APIs**:
  - [ ] `/save-progress` to save video playback progress.
  - [ ] `/get-progress?video_id={id}` to retrieve playback progress.

### Middleware
- [ ] Implement middleware for:
  - [ ] JWT-based authentication.
  - [ ] Logging and error handling.

---

## Video Storage and Transcoding
### Setup
- [ ] Configure Cloudflare R2 for video storage.
- [ ] Set up a bucket for storing videos.
- [ ] Enable signed URLs for secure video delivery.

### Transcoding
- [ ] Install FFmpeg locally or in a Docker container.
- [ ] Write a script to:
  - [ ] Convert uploaded videos to HLS/DASH formats.
  - [ ] Generate adaptive bitrate streams.

### Integration
- [ ] Upload transcoded videos to Cloudflare R2.
- [ ] Save metadata (e.g., URL, resolution, duration) to MongoDB.

---

## Infrastructure and DevOps
### Docker
- [ ] Write Dockerfiles for:
  - [ ] Frontend.
  - [ ] Backend.
  - [ ] MongoDB and PostgreSQL.
  - [ ] FFmpeg (if running locally in a container).
- [ ] Set up a `docker-compose.yml` to orchestrate services locally.

### Cloudflare Configuration
- [ ] Set up CDN for fast video delivery.
- [ ] Configure DNS for frontend and backend URLs.
- [ ] Enable caching for static assets.

### Deployment
- [ ] Choose a VPS (e.g., DigitalOcean, AWS Lightsail).
- [ ] Deploy Docker containers for frontend, backend, and databases.
- [ ] Configure a reverse proxy (e.g., NGINX or Traefik).
- [ ] Set up HTTPS using Let's Encrypt.

### CI/CD
- [ ] Set up a GitHub Actions workflow for:
  - [ ] Linting and testing.
  - [ ] Building Docker images.
  - [ ] Deploying to the server.

### Monitoring and Logging
- [ ] Install and configure cAdvisor for container monitoring.
- [ ] Set up Grafana with Prometheus for metrics.
- [ ] Use ELK stack or Cloudflare logs for request monitoring.

---

## Testing
### Frontend
- [ ] Write unit tests for components using Svelte Testing Library.
- [ ] Test API integration using mocked responses.
- [ ] Perform cross-browser testing for the video player.

### Backend
- [ ] Write unit tests for API endpoints using Go's `testing` package.
- [ ] Add integration tests for database queries.

### Load Testing
- [ ] Use tools like Apache JMeter or k6 to simulate user load.

---

## Final Polishing
- [ ] Optimize video load times with CDN and caching.
- [ ] Ensure accessibility compliance (WCAG standards).
- [ ] Conduct security testing (e.g., OWASP checklist).
- [ ] Gather user feedback and make iterative improvements.

---

## Stretch Goals
- [ ] Implement a recommendation engine (e.g., based on tags or history).
- [ ] Add multi-profile support for user accounts.
- [ ] Enable live streaming using WebRTC.
- [ ] Build a mobile app version using SvelteKit or another framework.
