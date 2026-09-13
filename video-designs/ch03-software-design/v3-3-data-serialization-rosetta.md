---
video_id: V3.3
chapter: 3
title: "The Data Serialization Rosetta Stone: XML, JSON, and YAML Demystified"
composition_id: net226-v3-3-data-serialization-rosetta
duration_target: "5:30"
aspect: "16:9"
engine: codevideo
libraries: [prismjs, terminal-emulator]
blocks: [rosetta-three-editor-split, python-repl-run]
objectives:
  - Compare the syntax rules and structure of JSON, YAML, and XML.
  - Parse and serialize data structures in Python using `json`, `yaml`, and `xmltodict`.
  - Identify common syntax traps: YAML whitespace indentation and JSON trailing commas.
opens_with: cpcc-open
source_section: ch03 §3.5 & 3.6
---

# Video Design: V3.3 The Data Serialization Rosetta Stone

---

## Scene 1 — The Three Languages of Network Data (0:00–1:00)
**Visual:** A 3-way split screen in VS Code showing the exact same interface data represented in JSON (left), YAML (center), and XML (right).
**Narration:**
> Modern network APIs do not exchange raw CLI text strings. They exchange structured data.
>
> As a network automation engineer, you must be completely fluent in three serialization formats: JSON, YAML, and XML. Let's compare the exact same router interface across all three.

---

## Scene 2 — Dissecting JSON, YAML, and XML (1:00–3:00)
**Visual:** Zooming into each editor panel sequentially:
1. **JSON:** Highlighting curly braces `{ }`, quotes on keys, square brackets for arrays `[ ]`. A red error box highlights an illegal trailing comma: `, }`.
2. **YAML:** Highlighting clean whitespace indentation, dashes for lists `- `, and zero quotes. Demonstrating how a tab character breaks parsing.
3. **XML:** Highlighting opening and closing tags `<interface> ... </interface>`, hierarchical namespaces, and verbosity.
**Narration:**
> On the left: JSON. JSON is the universal language of REST APIs. Notice strict syntax: all keys must be double-quoted strings, and a single trailing comma will break the parser.
>
> In the center: YAML. Highly human-readable, which is why it's used for Ansible playbooks and Docker files. But beware: YAML is strictly whitespace indented. Never use tabs—always use spaces.
>
> On the right: XML. Verbose, with opening and closing tags. While older, XML remains the foundational encoding for NETCONF.

---

## Scene 3 — Parsing into Python Data Structures (3:00–4:45)
**Visual:** Python interactive REPL (`python3`) in terminal:
```python
>>> import json, yaml, xmltodict
>>> raw_json = '{"name": "GigabitEthernet1", "enabled": true}'
>>> data = json.loads(raw_json)
>>> print(data["name"], data["enabled"])
GigabitEthernet1 True
>>> raw_yaml = "name: GigabitEthernet1\nenabled: true"
>>> yaml_data = yaml.safe_load(raw_yaml)
>>> print(yaml_data["enabled"])
True
>>> raw_xml = "<interface><name>Gi1</name></interface>"
>>> xml_data = xmltodict.parse(raw_xml)
>>> print(xml_data["interface"]["name"])
Gi1
```
**Narration:**
> The beauty of Python is that all three formats parse into the exact same native Python data structures: dictionaries, lists, and booleans.
>
> Use `json.loads()` for JSON strings. Use `yaml.safe_load()` for YAML. And use the fantastic `xmltodict` library to turn XML trees into Python dictionaries in one line of code.

---

## Scene 4 — Summary & Challenge (4:45–5:30)
**Visual:** Comparison matrix summarizing best use cases: JSON for REST APIs, YAML for configuration templates, XML for NETCONF.
**Narration:**
> Master the conversion between these three formats, and you can program any network device on earth. Next, let's learn how to test our parsing code using Test-Driven Development.
