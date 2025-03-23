---
title: "TMUX Project Aliases"
tags: ["dev", "tmux", "automation", "bash"]
---

# TMUX Project Aliases  

## Goal  
For each project in my `dev` folder, I want to create an alias that:  
1. Opens that project in a new TMUX window.  
2. If the project contains subfolders, each subfolder should also have an alias.  
3. The subfolder should open in a separate pane inside the same TMUX window.  

## Implementation Plan  
- Write a script to scan the `dev` folder and generate aliases dynamically.  
- Use `tmux new-window` to create a new window for the main project.  
- Use `tmux split-pane` to open subfolders in smaller panes inside the same TMUX window.  
- Store the aliases in a `.bashrc` or `.zshrc` file for easy execution.  

## Sample Script  

```bash
#!/bin/bash

DEV_DIR=~/dev

# Function to create a TMUX window and split panes for subfolders
create_tmux_session() {
  local project_name=$(basename "$1")
  tmux new-window -n "$project_name" -c "$1"

  # Find subdirectories and open them in panes
  local subfolders=($(find "$1" -maxdepth 1 -type d | tail -n +2))
  for sub in "${subfolders[@]}"; do
    tmux split-window -v -c "$sub"
    tmux select-layout tiled  # Arrange panes neatly
  done
}

# Generate aliases dynamically
generate_aliases() {
  for project in "$DEV_DIR"/*; do
    if [ -d "$project" ]; then
      alias_name=$(basename "$project")
      echo "alias $alias_name='tmux new-session -A -s $alias_name -c $project'" >> ~/.bash_aliases
    fi
  done
}

generate_aliases
source ~/.bash_aliases
echo "TMUX aliases generated."