---
title: "Moon Lander Keyboard Layers for Aerospace Mode"
tags: ["moonlander", "keyboard-layout", "aerospace", "terminal", "super-whisper", "workflow"]
---

# Moon Lander Keyboard Layers for Aerospace Mode

## Concept  
Create additional **keyboard layers** on the Moon Lander that emulate typical movement and window control patterns used in aerospace-like workflows.

## Goals  
- Build **custom screen layers** for terminal navigation, browser integration, and window movement.  
- Move away from standard `ctrl + IJKLH` motions, which don't align well with the Moon Lander layout or muscle memory.  
- Enable **more intuitive control schemes** tailored to context (e.g. terminal vs streaming browser view).  

## Features to Consider  
- Dedicated **"aerospace mode"** layer with keys mapped for context-specific navigation.  
- Integrate **Super Whisper** for voice-controlled mode switching or quick context jumps.  
- **Center right-hand button** acts as a "shared control" for pulling in frequently used screens (e.g. terminal, browser view).  
- Differentiate between **screen navigation** and **application switching**, rethink how each works within this context.  

## Notes  
- Use layered tap/hold behavior for multipurpose keys.  
- Test integration with your current terminal + browser setup.  
- Create visual layout map for reference in the firmware config.

## Next Steps  
- [ ] Sketch a layout for the new Aerospace Layer.  
- [ ] Define voice commands with Super Whisper that could trigger layout/context changes.  
- [ ] Prototype window movement with simplified shortcuts or Home Row logic.  
- [ ] Map the center button to open shared context screens.  

## Related Notes  
- [[Super Whisper Speech-to-Action Protocol for Streaming App]]  
- [[Keyboard Ergonomics and Movement Mapping]]  
- [[Terminal + Browser Hybrid Workflows]]