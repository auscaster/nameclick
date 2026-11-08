# Nameclick by Sourcey

Find a person's email address from their LinkedIn profile, their GitHub login, or their name on any
page, X and YouTube included, enriched with their roles and company. The card shows who matched, so
you know it is the right person before you write.

- **Extension:** on the [Chrome Web Store](https://chromewebstore.google.com/detail/hnknkbjoidfdjocmdjjfchiggmgmcojl),
  which Brave, Arc and Opera install from too; Edge and Firefox list it once their stores approve
  it. On the web, the [LinkedIn email finder](https://sourcey.com/linkedin-email-finder) does the
  same lookup from a profile's address.
- **Agents:** the hosted MCP server at `https://mcp.nameclick.co/mcp`, registry name
  `co.nameclick/nameclick`.
- **API:** described at [api.nameclick.co/openapi.json](https://api.nameclick.co/openapi.json).

## The MCP server

| Tool | Does |
| --- | --- |
| `find_contact` | Finds who a person is and their email address, from a LinkedIn address, an email, a GitHub login, a full name with their company or its domain, or their name on a page. One lookup is spent only the first time an email address on record is shown for someone. |
| `get_contact` | Reopens a person you found before, free. |
| `get_services` | The lookup API, for agents that call it directly. Uses no lookups. |

The `find_email` prompt gives clients a slash command.

Add `https://mcp.nameclick.co/mcp` as a connector in Claude, ChatGPT, Cursor, VS Code or any app
that signs in to MCP servers. It asks you to sign in with Google and approve the app, and every
lookup it makes is on your account, the same as the extension's.

An agent that can't sign in, such as a script, sends a key in the `Authorization` header instead,
as `Bearer <key>`, from the extension's settings under "Use Nameclick in your agent":

```json
{
  "mcpServers": {
    "nameclick": {
      "type": "http",
      "url": "https://mcp.nameclick.co/mcp",
      "headers": { "Authorization": "Bearer <your Nameclick key>" }
    }
  }
}
```

The [skill](skills/nameclick/SKILL.md) teaches an agent to resolve the person first and to look up
only the person the user asked about.

## Privacy

Nameclick reads a profile's address, or a selected name and the text around it, only when you
press. The [privacy policy](https://sourcey.com/nameclick/privacy) says what is kept, and anyone in
it can [ask to be removed](https://sourcey.com/nameclick/remove).

## Licence

Apache-2.0. See [LICENSE](LICENSE).
