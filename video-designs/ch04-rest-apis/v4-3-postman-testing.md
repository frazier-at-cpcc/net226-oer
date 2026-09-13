---
video_id: V4.3
chapter: 4
title: "API Testing with Postman: Collections, Environments, and Automated Tests"
composition_id: net226-v4-3-postman-testing
duration_target: "6:00"
aspect: "16:9"
engine: codevideo
libraries: [prismjs, terminal-emulator]
blocks: [postman-ui-walkthrough, test-script-editor]
objectives:
  - Formulate and execute authenticated REST API calls in Postman.
  - Configure dynamic environment variables for token management.
  - Author automated JavaScript test assertions in Postman.
opens_with: cpcc-open
source_section: ch04 §4.5
---

# Video Design: V4.3 API Testing with Postman

---

## Scene 1 — Why Postman? (0:00–1:00)
**Visual:** Postman application launches on the DEVASC desktop.
**Narration:**
> When you integrate a new network API, never start by writing Python code. If your script fails, you won't know if the bug is in your Python syntax or in your HTTP headers.
>
> Postman is the premier API exploration tool. It lets you construct requests visually, inspect raw headers, manage authentication tokens, and run automated tests before writing a single line of application code.

---

## Scene 2 — Environments & Variables (1:00–2:45)
**Visual:** Creating an Environment named `DevNet-Sandbox`. Setting variables:
`base_url`: `https://sandboxdnac.cisco.com`
`auth_token`: `(empty)`
Authoring a request in a Collection: `POST {{base_url}}/dna/system/api/v1/auth/token`.
Sending request; receiving `200 OK` with JSON token payload.
**Narration:**
> Never hardcode URLs or tokens inside your requests. Use Postman Environments.
>
> We define `{{base_url}}` pointing to our sandbox controller.
>
> In our authentication request, we supply HTTP Basic credentials. When we hit Send, the Catalyst Center controller responds with a temporary Bearer token valid for one hour.

---

## Scene 3 — Automating Token Extraction via JavaScript (2:45–4:30)
**Visual:** Clicking the 'Tests' tab in Postman. Writing JavaScript:
```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

var jsonData = pm.response.json();
pm.environment.set("auth_token", jsonData.Token);
```
Hitting Send. Green test passes: `PASS: Status code is 200`. The environment variable `{{auth_token}}` is automatically populated!
**Narration:**
> Look at how powerful Postman test scripts are. In the Tests tab, we write two lines of JavaScript.
>
> The first asserts that our status code is 200.
>
> The second parses the response JSON, grabs the temporary token string, and automatically saves it into our `auth_token` environment variable.
>
> Now, every subsequent request in our collection can use `{{auth_token}}` in its Authorization header without any manual copying and pasting!

---

## Scene 4 — Calling Device Inventories (4:30–6:00)
**Visual:** Executing `GET {{base_url}}/dna/intent/api/v1/network-device`. Adding header `X-Auth-Token: {{auth_token}}`. Receiving 200 OK with list of network switches and routers.
**Narration:**
> Now we call `/dna/intent/api/v1/network-device`. Notice our header uses our dynamic variable. We hit Send, and within 200 milliseconds, the controller returns the complete hardware inventory.
>
> Once your requests succeed in Postman, translating them to Python is trivial. In our next video, we'll build a resilient Python API client.
