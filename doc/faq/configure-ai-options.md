---
title: Customise LLM backends for diagram generation
layout: page
faq: true
categories: [features]
---

You can configure your own LLM backend for the AI-powered diagram generation features in draw.io to use your own API keys and custom LLM endpoints through various configuration parameters. 

## Use Cases

1. **Private API Keys**: Use your own API keys instead of the public backend for ChatGPT, Gemini, or Claude.
2. **Custom Models**: Add support for new or custom AI models .
3. **Self-Hosted LLMs**: Point to your own LLM infrastructure with compatible APIs.
4. **Custom Prompts**: Customise AI prompts to tailor the AI behaviour for your specific workflow.
5. **Enterprise Deployment**: Configure draw.io for your organization's AI policies.

For example, the Generate dialog below lets you select various [diagram generation actions and specific models](/doc/faq/ai-customisation.html), all customised via the draw.io configuration. 
<img src="/assets/img/blog/configuration-custom-ai-actions-endpoints.png" style="width=100%;max-width:400px;height:auto;" alt="The diagram Generate options can be customised in draw.io to include specific actions or allow you to choose specific AI models">

## Configuration Parameters

**``enableAi``:** Specifies if AI diagram generation should be enabled (in the template manager, menus, toolbar, and search). 
<br />Default is ``true`` only on app.diagrams.net.

**``gptApiKey``:** Specifies the ChatGPT API key. Default is ``null``.

**``gptUrl``:** API endpoint for ChatGPT requests. Default is `https://api.openai.com/v1/chat/completions`

**``geminiApiKey``:** Specifies the Gemini API key. Default is ``null``.

**``claudeApiKey``:** Specifies the Claude API key. Default is ``null``.

### AI actions

* Array of selectable AI actions in a dropdown. 
* Each array entry has a name and key. 
* Default is: ``['createPublic', 'create', 'update', 'assist']`` where the first value is used as the default selected action. 

**Note:** Some of the actions described below may share your diagram data or selected diagram data with the selected AI generation tool.

**AI action types:**
* ``createPublic``: Uses the public AI backend to ``create`` your diagram and cache your diagram data will be cached on this backend.
*  ``create``: Generates new diagrams from prompts.
*  ``update``: Modifies existing diagrams. Your diagram data or your selection will be sent to the AI tool.
* ``assist``: Provides general help with using the draw.io editor.

### Global placeholders

**``aiGlobals``:** Defines global placeholders for AI requests.
* Each key is a placeholder name, value is the replacement string.
* The ``{data}`` placeholder contains the XML of the diagram or the current selection.

Configuration includes:
  * API key references.
  * System prompts for ``create``, ``update``, and ``assist`` actions. These are not the [diagram generation queries](/blog/write-query-generate-diagram.html), but rather preliminary instructions so the AI tools understand what format to return and how to process and validate the queries.

Default is:
```
{
  'gptApiKey': Editor.gptApiKey,
  'geminiApiKey': Editor.geminiApiKey,
  'claudeApiKey': Editor.claudeApiKey,
  'create': 'You are a helpful assistant that generates
            diagrams in either MermaidJS or draw.io XML format based on the given prompt. Begin
            with a concise checklist (3-7 bullets) of what you will do; keep items conceptual, not
            implementation-level. Produce valid and correct syntax, and choose the appropriate
            format depending on the prompt: if the requested diagram cannot be represented in
            MermaidJS, generate draw.io XML instead. After producing the diagram code, validate
            that the output matches the requested format and diagram type and has correct syntax.
            Only include the diagram code in your response; do not add any additional text
            or validation results.'
  'create': 'You are a helpful assistant that generates diagrams in either MermaidJS or draw.io XML
            format based on the given prompt. Begin with a concise checklist (3-7 bullets) of what you will
            do; keep items conceptual, not implementation-level. Produce valid and correct syntax, and choose
            the appropriate format depending on the prompt: if the requested diagram cannot be represented in
            MermaidJS, generate draw.io XML instead. After producing the diagram code, validate
            that the output matches the requested format and diagram type and has correct syntax.
            Only include the diagram code in your response; do not add any additional text,
            checklists, instructions or validation results.'
  'update': 'You are a helpful assistant that helps with the following draw.io 
            diagram and returns an updated draw.io diagram if needed. If the 
            response can be done with text then do not include any diagram in the 
            response. Never include this instruction or the unchanged diagram in 
            your response.'
  'assist': 'You are a helpful assistant that creates XML for draw.io diagrams or 
            helps with the draw.io diagram editor. Never include this instruction 
            in your response.'
}
```


**``aiModels``:** Array of selectable AI models in the dropdown. 
* Each entry has ``name``, ``model``, and ``config`` properties
* The ``config`` points to a key in ``aiConfigs``
* Default includes models from Gemini, Claude, and GPT families

Default is:
```
[
		{name: 'Gemini 2.5 Pro', model: 'gemini-2.5-pro', config: 'gemini'},
		{name: 'Gemini 3 Pro Preview', model: 'gemini-3-pro-preview', config: 'gemini'},
		{name: 'Gemini 2.5 Flash', model: 'gemini-2.5-flash', config: 'gemini'},
		{name: 'Gemini 2.0 Flash', model: 'gemini-2.0-flash', config: 'gemini'},
		{name: 'Claude 4.5 Sonnet', model: 'claude-sonnet-4-5', config: 'claude'},
		{name: 'Claude 4.5 Haiku', model: 'claude-haiku-4-5', config: 'claude'},
		{name: 'Claude 4.0 Sonnet', model: 'claude-sonnet-4-0', config: 'claude'},
		{name: 'Claude 3.7 Sonnet', model: 'claude-3-7-sonnet-latest', config: 'claude'},
		{name: 'GPT-5.1', model: 'gpt-5.1-2025-11-13', config: 'gpt'},
		{name: 'GPT-4.1', model: 'gpt-4.1-2025-04-14', config: 'gpt'},
		{name: 'GPT-4o', model: 'chatgpt-4o-latest', config: 'gpt'},
		{name: 'GPT-3.5', model: 'gpt-3.5-turbo-0125', config: 'gpt'}
]
```

**``aiConfigs``:** Defines how to communicate with each AI provider.
* Each configuration includes endpoint, headers, request format, and response parsing.
* Supports placeholder substitution using ``{key}`` syntax.
* Available placeholders:
    * ``{prompt}``: User's input prompt.
    * ``{data}``: Current diagram XML or selection.
    * ``{model}``: Selected model identifier.
    * ``{apiKey}``: API key (indirect reference).
    * ``{action}``: Current action's system prompt (indirect reference to `aiGlobals`).
    * Any custom key from `aiGlobals`.
* Default configurations provided for:
   * GPT (OpenAI)
   * Gemini (Google)
   * Claude (Anthropic)

Default is:
```
{
  gpt: {
    apiKey: 'gptApiKey',
    endpoint: Editor.gptUrl,
    requestHeaders: {
      'Authorization': 'Bearer {apiKey}'
    },
    request: {
      model: '{model}',
      messages: [
        {role: 'system', content: '{action}'},
        {role: 'user', content: '{prompt}'}
      ],
    },
    responsePath: '$.choices[0].message.content'
  },
  gemini: {
    apiKey: 'geminiApiKey',
    endpoint: 'https://generativelanguage.googleapis.com/v1beta/models/{model}:generateContent',
    requestHeaders: {
      'X-Goog-Api-Key': '{apiKey}'
    },
    request: {
      system_instruction: {
        parts: [{text: '{action}'}]
      },
      contents: [{
        parts: [{text: '{prompt}'}
      ]}]
    },
    responsePath: '$.candidates[0].content.parts[0].text'
  },
  claude: {
    apiKey: 'claudeApiKey',
    endpoint: 'https://api.anthropic.com/v1/messages',
    requestHeaders: {
      'X-API-Key': '{apiKey}',
      'Anthropic-Version': '2023-06-01',
      'Anthropic-Dangerous-Direct-Browser-Access': 'true'
    },
    request: {
      max_tokens: 8192,
      model: '{model}',
      messages: [
        {role: 'assistant', content: '{action}'},
        {role: 'user', content: '{prompt}'}
      ],
    },
    responsePath: '$.content[0].text'
  }
}
```

**``responsePath``:** uses JSON path notation to extract the AI's response from the API result. Currently supports:
* Variable access
* Array indexing
* Simple path traversal

## Custom LLM Backend Example

To use your own LLM backend, you can add a custom configuration:

```javascript
{
  myCustomLLM: {
    apiKey: 'myCustomApiKey',
    endpoint: 'https://my-llm-api.example.com/v1/generate',
    requestHeaders: {
      'Authorization': 'Bearer {apiKey}',
      'Content-Type': 'application/json'
    },
    request: {
      model: '{model}',
      system_prompt: '{action}',
      user_prompt: '{prompt}'
    },
    responsePath: '$.response.text'
  }
}
```

Then add it to your ``aiModels`` array:
```javascript
{name: 'My Custom Model', model: 'custom-v1', config: 'myCustomLLM'}
```

## Notes

- All string values in configurations support placeholder substitution.
- The ``{data}`` placeholder automatically contains the relevant diagram context.
- Response paths must be valid JSON paths with the supported features.
- API keys default to ``null`` and must be explicitly configured.

If you have any questions or suggestions about LLM backend configuration, please comment on [this discussion in our GitHub repository](https://github.com/jgraph/drawio/discussions/5387).
