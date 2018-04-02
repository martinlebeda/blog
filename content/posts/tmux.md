---
title: "Tmux"
date: 2018-04-02T20:15:55+02:00
draft: true
---

Tmux patří mezi programy, které jsem dlouho pomíjel, ale nyní nechápu jak jsem
bez nich mohl žít. Terminálový multiplexer je vynikající software pro práci s
terminálovými sessions.

<!--more-->

Používám jej z mnoha důvodů a mezi hlavní patří:

- Možnost odpojit session od terminálu aniž by se ukončili v ní spuštěné
  programy.
- Možnost rozdělit obrazovku terminálu na jednotlivé dlaždice, podobně jako to
  dělají tilling managery.
- Výborné ovládání terminálu z klávesnice. Včetně vybírání textu a kopírování
  do schránky.
- Možnost scriptování session, přímo ze spouštěných scriptů nebo příkazů
  zapsaných v terminálu.
  
## Nastavení 

Vybrané části z nastavení (celé nastavení je tady TODO)

```
# default shell
set -g default-shell /usr/bin/zsh
# use 256 term for pretty colors
set -g default-terminal "screen-256color"
# increase scroll-back history
set -g history-limit 50000

set -g status off
set-option -g bell-action any
set-option -g visual-bell off

set-window-option -g mode-keys vi

bind P paste-buffer
bind-key -t vi-copy 'v' begin-selection
# bind-key -t vi-copy 'y' copy-selection
bind-key -t vi-copy 'r' rectangle-toggle
bind -t vi-copy y copy-pipe 'xclip -in -selection clipboard'

# window/terminal title
set-option -g set-titles on
set-option -g set-titles-string "#S (#I/#{session_windows}): #W"
# set-window-option -g automatic-rename on
# set-window-option -g automatic-rename-format '#{window_index}: #{pane_current_command} #{pane_current_path}'
# set-window-option -g window-status-current-format '#{window_index}: #{pane_current_command} #{pane_current_path} |'

# mouse setup
# set-window-option -g mode-mouse on
set -g mouse on

# Getting interesting now, we use the vertical and horizontal
# symbols to split the screen
bind | split-window -h
bind - split-window -v
unbind t
bind t set status on

# pro tmux > 2.5
# bind-key -T copy-mode-vi v send-keys -X begin-selection
# bind-key -T copy-mode-vi y send-keys -X copy-selection
# bind-key -T copy-mode-vi r send-keys -X rectangle-toggle
# bind -T copy-mode-vi y send-keys -X copy-pipe-and-cancel 'xclip -in -selection clipboard'

# Scroll up/down by 1 line, half screen, whole screen
# bind -T copy-mode-vi M-Up              send-keys -X scroll-up
# bind -T copy-mode-vi M-Down            send-keys -X scroll-down
# bind -T copy-mode-vi M-PageUp          send-keys -X halfpage-up
# bind -T copy-mode-vi M-PageDown        send-keys -X halfpage-down
# bind -T copy-mode-vi PageDown          send-keys -X page-down
# bind -T copy-mode-vi PageUp            send-keys -X page-up


# bind p paste-buffer
# bind C-p choose-buffer
# bind-key P command-prompt -p 'save history to filename:' -I '~/tmux.history' # 'capture-pane -S -32768 ; save-buffer %1 ; delete-buffer'
#
```

## Základní ovládání oken a panelů

## Ovládání z příkazové řádky

## 
