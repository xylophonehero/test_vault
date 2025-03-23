---
title: "Speech-to-Action Protocol for Streaming App"
tags: ["speech-to-text", "xstate", "ai-agent", "streaming-app", "voice-control", "model-context"]
---

# Speech-to-Action Protocol for Streaming App

## Vision  
Build a **Super-Whisper**-powered speech-to-text system integrated with the streaming app that enables **voice-controlled interactions** through a shared model context protocol. The goal is to convert speech into actionable events in the app.

## Core Workflow  
1. **Speech input** is transcribed to text via Whisper.  
2. Transcription is interpreted using an AI agent trained on the app’s **state machine model context**.  
3. The AI selects which **state machine** and **event** to trigger.  
4. The app responds accordingly — e.g.  
   - “Start presentation” → triggers `startPresentation`  
   - “Next slide” → triggers `nextSlide`  
   - “Send a message to Sarah” → routes a message  
   - “Answer this question” → generates an AI-powered reply  

## Model Context Protocol  
To support this, we need a **structured schema-based protocol** that:  
- **Indexes all active state machines**  
- Defines each machine’s **actions, events, descriptions, and capabilities**  
- Acts as the **context for training** the AI agent  

This would cover both static events (e.g. `startWebinar`, `stopWebinar`) and dynamic ones (e.g. `sendChatMessage`, `replyToQuestion`, `bringOnStage`).

## Functional Requirements  
- **Schema support**: Add rich descriptions and event metadata directly to state machines  
- **Agent logic**: Interpret transcription and map it to a specific event  
- **Chat-like API**: Call an agent from the frontend via a protected **Ruby service**  
- **Rate limiting**: Protect the AI endpoint from abuse or overuse during webinars  

## Experimental Ideas  
- Try integrating Gladiator or a similar tool to test sending prompts and receiving text back  
- Explore **auto-answering questions** using AI trained on previous answers  
- Enable post-webinar AI summarisation or analysis  

## Next Steps  
- [ ] Design the model context schema  
- [ ] Prototype Whisper integration with basic commands  
- [ ] Build the Ruby API for handling requests  
- [ ] Integrate the system with state machine definitions  
- [ ] Benchmark usage and AI call rates per webinar  

## Related Notes  
- [[ActiveSystems: Managing Groups of State Machines]]  
- [[TypeScript Caching Tool for Machine File Types]]  
- [[Webinar Agenda Component Automation]]