# Wezterm Configuration

Source: [Wezterm Configuration](https://wezterm.org/config/files.html)

-- ~/.wezterm.lua
local wezterm = require 'wezterm'
local config = wezterm.config_builder()

-- Font settings
config.font = wezterm.font 'JetBrains Mono'
config.font_size = 16.0

-- Color scheme
config.color_scheme = 'Tokyo Night'

-- Window settings
config.window_background_opacity = 0.95
config.window_decorations = "RESIZE"
config.window_padding = {
  left = 10,
  right = 10,
  top = 10,
  bottom = 10,
}

-- Tab bar settings
config.hide_tab_bar_if_only_one_tab = true
config.tab_bar_at_bottom = false

-- Scrollback
config.scrollback_lines = 10000

-- OS detection
local is_mac = wezterm.target_triple:find("darwin") ~= nil
local is_windows = wezterm.target_triple:find("windows") ~= nil
local is_linux = wezterm.target_triple:find("linux") ~= nil

-- OS-specific font settings
if is_mac then
  config.font = wezterm.font 'SF Mono'
  config.font_size = 14.0
elseif is_windows then
  config.font = wezterm.font 'Cascadia Code'
  config.font_size = 12.0
  -- Set WSL as default shell
  config.default_prog = { 'wsl.exe' }
else
  config.font = wezterm.font 'JetBrains Mono'
  config.font_size = 13.0
end

local act = wezterm.action

config.keys = {
  -- Pane splitting
  { key = 'd', mods = 'CMD', action = act.SplitHorizontal { domain = 'CurrentPaneDomain' } },
  { key = 'd', mods = 'CMD|SHIFT', action = act.SplitVertical { domain = 'CurrentPaneDomain' } },

  -- Pane navigation
  { key = 'h', mods = 'CMD|SHIFT', action = act.ActivatePaneDirection 'Left' },
  { key = 'l', mods = 'CMD|SHIFT', action = act.ActivatePaneDirection 'Right' },
  { key = 'k', mods = 'CMD|SHIFT', action = act.ActivatePaneDirection 'Up' },
  { key = 'j', mods = 'CMD|SHIFT', action = act.ActivatePaneDirection 'Down' },

  -- Pane resize
  { key = 'LeftArrow', mods = 'CMD|ALT', action = act.AdjustPaneSize { 'Left', 5 } },
  { key = 'RightArrow', mods = 'CMD|ALT', action = act.AdjustPaneSize { 'Right', 5 } },

  -- Tab operations
  { key = 't', mods = 'CMD', action = act.SpawnTab 'CurrentPaneDomain' },
  { key = 'w', mods = 'CMD', action = act.CloseCurrentPane { confirm = true } },

  -- Copy mode (vi-style)
  { key = 'v', mods = 'CMD|SHIFT', action = act.ActivateCopyMode },
}

return config
