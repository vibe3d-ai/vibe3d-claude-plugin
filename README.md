# Vibe3D

![Vibe3D logo](assets/icon.png)

Draft for architectural design visualization in Claude. This bundle is not yet listed in the Claude directory. Directory-policy eligibility, distribution, and full Claude workflow testing remain pending.

Vibe3D connects Claude to your private architectural projects. Render a model-view image, revise materials or lighting, enhance an architectural image, and compare saved versions. The bundle contains one workflow skill and a reference to Vibe3D's hosted MCP server. It has no local server, executable scripts, hooks, or embedded credentials.

## Connect

You need a Vibe3D account. Add the bundled Vibe3D connector from the plugin's Connectors tab in Claude and sign in through Vibe3D's OAuth consent screen. Claude Code loads the MCP reference with the plugin; complete authentication through its MCP controls.

The server is https://basecamp.vibe3d.ai/mcp. Dynamic client registration and PKCE handle sign-in; users do not need the private ChatGPT client secret or a developer API key. Remote MCP access tokens last one hour, and a connection must be authorized again after seven days.

Vibe3D currently allows one active MCP connection per account. Connecting another MCP client replaces that account's previous MCP connection, including its refresh capability. Use separate review/test accounts when integrations must remain connected independently.

## Use it

- “Use Vibe3D to find my Courtyard Study project and open its latest saved scene.”
- After uploading an architectural model view through Studio: “Render this in warm daylight in a new private project called Courtyard Study.”
- “In that Vibe3D scene, change the walls to sage green and preserve the rest of the design.”
- “Enhance this architectural render's realism without replacing the source.”

In a compatible MCP Apps host, open Studio and use **Choose image** to select a PNG or JPEG from your device. The limit is 10 MiB and 40 megapixels. Uploading an image alone does not request a render. If the embedded panel is unavailable, use the returned Vibe3D web-editor link or an existing saved scene.

Do not assume that a picture attached to a Claude conversation is accessible to this connector. Claude Code can use a user-specified local file only when its authorized file and HTTP tools can transfer the actual bytes. The service does not read Claude's memory, chat history, or attachment library.

Rendering, revisions, and enhancement use Vibe3D credits. Project browsing and image uploads do not spend render credits. AI-generated visualizations are design aids, not dimensionally accurate CAD/BIM models or construction/engineering approvals. This connector exposes no video or 3D-model generation tools.

## Privacy and sharing

Tool calls send the selected project/scene identifiers, architectural images, design instructions, and requested account actions to Vibe3D. Vibe3D stores projects, source images, generated versions, and related account records, and uses third-party AI processors for generation as described in its privacy policy. Studio transfers selected images through Vibe3D's signed storage URLs. The bundle itself adds no separate storage or analytics service.

New projects and images are private. Sharing needs a separate explicit request. Anyone with a shared scene link who signs in to Vibe3D can view that scene and all its versions. Revoking sharing restores owner-only access. The normal web-editor link is not a sharing link.

- [Privacy policy](https://vibe3d.ai/privacy-policy)
- [Terms](https://vibe3d.ai/terms-of-service)
- [Support](https://app.vibe3d.ai/support): support@vibe3d.ai

## Troubleshooting

If authorization expires, reconnect the connector. If another MCP client was connected to the same Vibe3D account, that can invalidate this connection. Inspect the saved project before retrying an uncertain render; a delayed response is not a new request. For insufficient credits or provider failures, use the returned error and do not claim a result was created.

To revoke the active MCP connection, open Vibe3D → Profile → Connected apps. Removing the plugin or clearing a client's credentials is not proof of server-side revocation. Revoking MCP access does not delete your projects or sign you out of the Vibe3D web app.

## License

The manifest, connector configuration, documentation, and workflow skill are licensed under the [MIT License](LICENSE). The Vibe3D name and logo are excluded; branding rights are reserved and no trademark rights are granted. This license does not cover Vibe3D's hosted service, application, or backend code.

## Distribution status

The owner has approved MIT for the text and configuration and a private preparation repository at [vibe3d-ai/vibe3d-claude-plugin](https://github.com/vibe3d-ai/vibe3d-claude-plugin). Public repository visibility and directory publication have not been approved. This bundle is not ready for directory submission. Directory eligibility and complete workflow coverage must be resolved before publication; do not treat the example prompts as evidence that every operation has been tested.
