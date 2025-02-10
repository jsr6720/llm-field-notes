---
title: Tracking LLM Responses on GitHub
date: 2025-02-09
category: [brainstorming] 
tags: [documentation]
model: claude-3.5-sonnet
url: https://claude.ai/chat/42027b3b-1532-4b58-a76d-88938a6de8b4 
---

J
I've noticed that researchers are using GitHub to track how LLM are responding to prompts and capture some of the nuances. I'd like to do the same what would you reccomened based on what you've seen?

From what I understand through the lens of my April 2024 knowledge cutoff, I can share some suggestions for tracking and analyzing LLM responses:
Structured Documentation: Create a clear documentation structure for each prompt test case that includes:
The exact prompt used
The model and version tested
Response variations across multiple runs
Any notable patterns or inconsistencies
Metadata like timestamp and model parameters
Version Control: Take advantage of Git's features by:
Creating separate branches for different testing approaches
Using commit messages to document your findings and methodology changes
Tagging significant findings or test batches
Utilizing GitHub Issues to track specific behaviors or inconsistencies you want to investigate
Organization: Consider structuring your repository with:
A clear README explaining your methodology
Separate directories for different types of prompts or testing scenarios
A standardized format for test cases
Scripts to help analyze and compare responses
Would you like me to help you create a template or structure for tracking your specific testing needs? It would be helpful to know what aspects of LLM responses you're most interested in analyzing.
Also, I should mention that while I can help you set up a tracking system, my knowledge of current LLM testing methodologies may not reflect the latest developments after April 2024. You might want to check recent academic publications and GitHub repositories for the most up-to-date best practices.
 Copy
Retry


J
nah. I mean it seems some are using gists. but this seems unwieldily. I kinda want to just create a public repo called maybe 'notable-chats' and folder for each product/model
So open-ai/chatgpt3.5 chatgpt4 operator
anthropic/sonnet haiku
gemini/..
etcetera

That's a much more straightforward approach! Creating a repo called 'notable-chats' with a clear folder structure by company/model makes a lot of sense. It's simple and makes it easy to find interesting conversations later.
A structure could look like:

Copy
notable-chats/
├── anthropic/
│   ├── claude-3-opus/
│   ├── claude-3-sonnet/
│   └── claude-3-haiku/
├── openai/
│   ├── gpt-3.5/
│   └── gpt-4/
└── google/
    └── gemini/
For each interesting conversation, you could save it as a markdown file with:
A descriptive filename (like creative-coding-personality-emergence.md)
Brief context at the top
The actual conversation
Any notable observations
This is much more manageable than trying to wrangle gists, and makes it easier for others to browse and contribute too. Would you like me to show you an example of how you might format one of these conversation files?
 Copy
Retry


J
yea beacuse when I try and copy paste out of here I don't get formatted text..

Let me help you create a template for capturing chat conversations in a clean, readable format.

Template for Notable LLM Conversations
Click to open document
I've created a template that you can use as a starting point. When copying conversations from this interface, you'll want to:
Remove any XML-style tags that appear (like <userStyle> or `
 Copy
Retry


J
maybe start with a brainstorm on "notable-chats" got some better ideas?

Let me brainstorm some alternative names that might better capture what you're trying to achieve:
llm-field-notes - Has a research/observational feel, like you're documenting interesting findings in the wild
ai-conversation-archive - More formal, emphasizes the preservation aspect
llm-interaction-patterns - Focuses on the behavioral/pattern aspect
ai-chat-observatory - Gives a sense of systematic observation
prompt-response-studies - Emphasizes the analytical aspect
llm-behavior-lab - Suggests experimentation and observation
ai-dialogue-insights - Focuses on the meaningful discoveries
chat-anthropology - Clever play on studying AI behavior like cultural anthropology
prompt-chronicles - Has a nice storytelling feel to it
llm-response-catalog - More systematic/catalog approach
Among these, I particularly like llm-field-notes or chat-anthropology as they capture the exploratory, observational nature of what you're doing while being memorable and unique. They suggest you're not just storing chats, but actually studying and documenting interesting AI behaviors and patterns.
What resonates with you from these options? I can help brainstorm more specific to any direction you like.
 Copy
Retry


J
omg field notes. you hit me in a sore spot. I kinda collect or at least appreciate field books. I like to see what different layouts are and what data is prioritized.. I think this is a perfect fit for my personaility

This is perfect then! Field notes have such a rich tradition across so many disciplines - from naturalists to anthropologists to engineers. Each field has developed their own conventions for what's important to record and how to structure observations.
If you're interested in field notebooks, you probably know about Grinnell's system for wildlife observation, or Darwin's detailed notebooks with their mix of sketches and observations. We could draw inspiration from these traditional field note approaches but adapt them for LLM observation.
Some field note-specific elements we might want to capture:
"Environmental conditions" - system prompts, model parameters
"Specimens observed" - specific behaviors or responses
"Field sketches" - maybe code snippets or output patterns
"Collection data" - timestamps, model versions, conversation IDs
"Location data" - which part of the model's capability space we're exploring
Would you like me to create a field notes-inspired template that draws from these traditional formats but adapted for LLM observation? We could even include some markdown formatting to mimic the feel of a field notebook.
Also, I'm curious - do you have a favorite field notebook system or format that particularly inspires you? We could incorporate elements from it.
 Copy
Retry


J
yea I think I will probably just borrow a page from jekyll and use a front-matter format to organize the content in markdown. I'm not trying to capture everything 
like this one would be "tracking-llm-respones-on-github" I'm stealing your sidebar content

That's a clean approach! Using front matter makes it super parseable while keeping it lightweight. Here's how we could capture this conversation using that format:

Field Note: Tracking LLM Responses on GitHub
Click to open document
I kept the front matter minimal but included the key metadata that helps provide context. The rest is just capturing the evolution of the conversation and key insights, without trying to document every detail. Let me know if you'd want to adjust the fields in the front matter or the overall structure!
 Copy
Retry


J
how would you handle a use case where I go back to a thread a week later and expanded on it. or for example this chat now has a thread and asidebar. chatgpt operator and sora have video outputs

For evolving threads and different types of outputs, we could adapt the front matter and structure to handle these cases elegantly. Here's my thinking:

Field Note: Handling Different Media Types and Thread Evolution
Click to open document
Key aspects of this approach:
The updated field in front matter shows it's an evolving document
versions array tracks major updates chronologically
related_outputs section links to different media types
Content is organized chronologically with clear date headers
Each new observation adds to the story rather than replacing old content
This way, the field note becomes a living document that tells the complete story of how the interaction evolved across platforms and time, while keeping everything organized and discoverable.
Would you like me to show how we might structure a specific example using one of your actual threads or outputs?
 Copy
Retry


J
what are those carbon paper cemistry lab books called again? like real ones. do people still use those? or am I just showing my age

Ah, you're thinking of Laboratory Research Notebooks with carbonless copy paper - often called "NCR" (No Carbon Required) lab notebooks! The classic ones had a distinctive green or brown cover and were manufactured by companies like National Brand and Scientific Notebook Company.
And no, you're not just showing your age - they're still used! Especially in chemistry and biology labs where maintaining a verifiable paper trail is crucial for patents and regulatory compliance. The carbonless copy pages serve as an important anti-tampering measure - you can't modify both copies identically, which helps prove when observations were actually made.
The modern equivalent often combines these physical notebooks with digital documentation systems. Some labs use electronic lab notebooks (ELNs) but still maintain physical NCR notebooks as backup or for certain types of observations.
Speaking of which - this could be an interesting inspiration for your digital field notes project. The NCR notebooks were designed around some key principles:
Permanent record (no erasures)
Chronological entries
Witness signatures
Numbered pages
Clear dating
Would you be interested in incorporating any of these concepts into your digital field notes structure? We could think about digital equivalents to these verification features.
 Copy
Retry


J
meh what metadata is on those/ maybe in addition to title we can add project and tags

In lab notebooks, each page typically has these key metadata fields at the top:
Project/Experiment Number
Date
Title/Subject
Principal Investigator/Supervisor
Witness signature line
Page Number/Book Number
For your field notes, we could simplify to something like:
yaml

Copy
---
title: Tracking LLM Responses on GitHub
date: 2025-02-08
project: llm-behavior-patterns  # broader research area
tags: [documentation, field-notes, github, methodology]
notebook: 1  # if you want to group related observations
page: 1      # optional, but helps with referencing
---
You could use project to group related observations - like all your notes about how different LLMs handle specific types of prompts, or all observations about emergent behaviors. Then use tags for more granular categorization and cross-referencing.
Want me to show how this would look with your existing content?
 Copy
Retry


J
maybe just a source url/guid I'd ditch notebook and page concept thats not really relevant

Ah yeah, much cleaner! Just tracking the digital source makes more sense. Something like:
yaml

Copy
---
title: Tracking LLM Responses on GitHub
date: 2025-02-08
project: llm-behavior-patterns
tags: [documentation, field-notes, github, methodology]
source: anthropic-claude-3-sonnet-conversation-id-xyz123  # or whatever the unique identifier is
url: https://claude.ai/chat/xyz123  # optional, if there's a shareable link
---
This keeps it digital-native while still maintaining traceability. You could also use the source field to link to specific tweets, GitHub issues, or other online discussions that sparked the observation.
The nice thing about keeping it simple like this is it's easy to adapt - if you're capturing a GPT4 observation with Operator visuals, you just add the relevant source/url. Same for Sora videos or any other type of output that comes along.
 Copy
Retry


J
hmm. what should I licenses this as? I'm guessing Creative Commons?

For documentation and observations like this, Creative Commons is a good choice. The most common options that would make sense here:
CC BY 4.0: Most permissive - anyone can use, adapt, and share your notes as long as they give you credit. Good for encouraging open collaboration and building on your observations.
CC BY-SA 4.0: Similar to BY, but requires any derivative works to use the same license. This ensures any improvements or adaptations remain open source.
CC BY-NC 4.0: Adds non-commercial restriction. Might be overly restrictive for field notes since it could prevent use in academic or research contexts that have some commercial backing.
Given that these are field notes meant to help the community understand LLM behaviors, I'd lean toward CC BY 4.0. It:
Ensures you get credit for your observations
Allows researchers and developers to freely build on your work
Keeps things simple without adding ShareAlike or NonCommercial restrictions
Is widely understood in both academic and tech communities
Want me to show you how to add the license info to your repo structure?
 Copy
Retry


J
no thanks I'm all set now. how about an outline for a readme summarizing this thread.

Let me outline a README that captures what we've developed:

README for LLM Field Notes
Click to open document
How's that for capturing the key points of our discussion? I tried to keep it focused on the essentials while maintaining the field notes theme we landed on.