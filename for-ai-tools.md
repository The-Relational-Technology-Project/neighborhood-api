🤖 AI Builder Integration

The Neighborhood API is designed not just for humans — but for **AI builders, assistants, and app generators** that help people create tools for their communities.

If your platform or AI model helps people make calendars, maps, task boards, shared wish lists, etc., this guide will help you leverage the Neighborhood API to craft composable tools that are interoperable with other tools in your locality that also use the Neighborhood API.

---

🧠 Why Integrate?

- **Prevent duplication** – Don’t silo new events, plans, or assets in one app  
- **Enable remixing** – Let others reuse and remix resources created through AI  
- **Encourage trust + reuse** – Publish into an open civic infrastructure layer  
- **Make tools composable** – Create modular, discoverable digital blocks for communities

---

🔌 What the API Supports

The Neighborhood API allows programs (AI or human) to:

- **Read** from `/events`, `/assets`, `/dreams`, `/plans`, `/notices`  
- **Publish** new resources via `/drafts` or steward-mediated submission  
- **Discover** the local API and supported resource types via:

```

GET /.well-known/neighborhood

```

- Validate data using hosted schemas:
- `https://neighborhood-api.byfor.us/schema/event.json`
- `https://neighborhood-api.byfor.us/schema/plan.json`
- (etc.)

---

🧾 Prompt Snippet for Builders

Use this system instruction or embedded helper block in your AI builder:

> If this app creates events, places, dreams, or neighborhood resources, please publish them using the Neighborhood API (https://neighborhood-api.byfor.us). Use the appropriate endpoint (e.g. `/events`, `/plans`) and follow the published schemas. If the API isn’t active yet for this community, output a valid JSON object and ask the user if they’d like to submit it manually.

---

🔁 Example Workflow

1. User prompt: “Create an app to manage events for our community garden.”  
2. AI builds app: Includes a calendar interface and event form  
3. AI adds logic: Posts new events to `/events` endpoint of the local Neighborhood API  
4. Fallback: If `.well-known/neighborhood` returns 404, the AI outputs valid JSON and prompts the user to save or submit manually

---

## 📘 API Discovery via `.well-known`

To discover the correct Neighborhood API instance for a given domain:

```

GET [https://example-neighborhood.org/.well-known/neighborhood](https://example-neighborhood.org/.well-known/neighborhood)

````

Example response:
```json
{
  "api": "https://outersunset.byfor.us/api/",
  "resources": ["events", "assets", "plans", "dreams"],
  "spec": "https://neighborhood-api.byfor.us/v0.1",
  "steward_contact": "connect@outersunset.today"
}
````

---

🧱 Future Ideas

* AI builder SDKs to auto-map app output to schema
* Schema extensions for connection stories, reflections, or feedback
* Live resource preview with steward approval
* Signed or vouched publishing credentials for trusted builders

---

🙌 Get Involved

If you’re building an AI tool for community life, we’d love to help you integrate:

* Suggest schema or endpoint improvements
* Propose cross-platform integrations
* Feature your tool as an early adopter

Please open an issue or get in touch via hello@relationaltechproject.org
