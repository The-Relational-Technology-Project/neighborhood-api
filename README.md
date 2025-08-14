# Neighborhood API – v0.1

A minimal, open, stewarded feed format for sharing **local events, assets, dreams, plans, and notices** across neighborhood websites, tools, and communities. 

Designed for care, interoperability, and remixability — this is quiet infrastructure for the relational web.

---

## 📘 Contents

- [Overview](#overview)
- [Use Cases](#use-cases)
- [Core Resource Types](#core-resource-types)
- [Endpoints](#endpoints)
- [Schemas](#schemas)
- [Stewardship Model](#stewardship-model)
- [Publishing Your Own Feed](#publishing-your-own-feed)
- [Roadmap](#roadmap)
- [License](#license)
- [Get Involved](#get-involved)

---

## 🧭 Overview

Most local knowledge lives in silos — flyers, Google Calendars, WordPress sites, inboxes. Neighborhood API is a simple spec for making that information **legible and reusable** across tools.

It defines common resource types like `events`, `assets`, `dreams`, and `plans`, with lightweight schemas and endpoints that can be hosted anywhere. 

This is not a platform. It’s connective tissue — a way for neighbors, tools, and stewards to stay in sync.

The Neighborhood API is designed both for humans and for AI builders that help humans create tools for their communities. We also acknowledge non-human animals, plants, fungi, mountains, rivers, spirit, and other beings, as the true builders of the layer 0 protocols of all neighborhoods.

---

## 💡 Use Cases

- A neighborhood website pulls events from local schools, orgs, and businesses
- Community tools like neighbor hubs and school PTA sites subscribe to local dreams + plans
- A community-run AI assistant answers "what's happening nearby this weekend?"
- A print newsletter automatically includes event listings + new community projects
- Local project planning teams tap into community assets and knowledge 

---

## 📦 Core Resource Types

### 🗓 Events
What’s happening when. Time-bound gatherings or activities.

### 🪑 Assets
What’s available to share or use. Physical or digital resources.

### 💭 Dreams
What we’re wishing for. Community desires or personal hopes.

### 🧭 Plans
What’s in motion. Projects with energy and stewards.

### 📢 Notices
What people should know. Civic alerts, announcements, calls for help.

🧠 *Knowledge* can be a subtype of assets — like how-tos, zines, or guides.

---

## 🔌 Endpoints (v0.1)

```
GET /meta
GET /events
GET /assets
GET /dreams
GET /plans
GET /notices

GET /events/{id}
GET /assets/{id}
...
```

All endpoints return JSON. Optional formats:

```
GET /events.ics
GET /events.rss
```

Query filters: `start_after`, `start_before`, `q`, `category`, `place_id`, `near`, `radius_km`

---

## 🧱 Schemas (v0.1 – Events only)

### Event (simplified example)
```json
{
  "id": "evt_blackbird_2025-09-12T1800",
  "name": "Sunset Book Club: Sci-Fi Night",
  "start": "2025-09-12T18:00:00-07:00",
  "end": "2025-09-12T19:30:00-07:00",
  "description": "Bring your favorite weird short story.",
  "category": ["literary", "community"],
  "place_id": "plc_blackbird_bookstore",
  "location": {
    "name": "Black Bird Bookstore",
    "address": "1234 Irving St, San Francisco",
    "lat": 37.75,
    "lng": -122.5
  },
  "url": "https://blackbirdbooks.com/events/sci-fi-night",
  "images": ["https://blackbirdbooks.com/images/sci-fi.jpg"],
  "organizer": {
    "name": "Black Bird Bookstore",
    "email": "events@blackbirdbooks.com"
  },
  "cost": "free",
  "source": {
    "publisher": "blackbirdbooks",
    "collected_at": "2025-08-13T09:00:03Z",
    "method": "ics",
    "license": "CC BY 4.0"
  }
}
```

---

## 🧶 Stewardship Model

Neighborhood APIs are maintained by **local stewards**. Each feed should have:

- A public `/meta` endpoint listing stewards and data sources
- A publisher allowlist (for ICS, RSS, JSON sources)
- Attribution and licensing for all entries
- An optional `POST /report` endpoint for content review

---

## 🚀 Publishing Your Own Feed

1. Start with public sources you already trust (Google Calendars, RSS, forms)
2. Normalize them into JSON per this spec
3. Publish as flat files or an API (e.g. with Express, FastAPI, or Cloudflare Workers)
4. Register the feed with community sites, tools, or apps

Soon: GitHub starter repo + sync scripts

---

## 🛣 Roadmap (v0.2+)

We're starting with a simple service for stewards:

- **📥 Paste-a-URL Resource Generator** – Turn links (ICS, RSS, Notion, etc.) into clean JSON resources
- **📤 One-click publishing** – Approve and publish resources to your feed from a web interface
- **🛠 Feed hosting and preview** – Serve and preview `/events`, `/plans`, and more without running your own infra

Next phases may include:
- Full schemas for all resource types
- Widget library (calendar, map, digest)
- Print/email digest generator
- ActivityPub support for public feeds

---

## ✍️ Get Involved

- Fork this repo and adapt for your neighborhood
- Suggest schema improvements or additions
- Add your feed to the registry (coming soon)
- Open an issue or email the stewards 

> Let’s build the infrastructure we need for our visions of community life.

