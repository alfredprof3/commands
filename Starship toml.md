<!-- Special characters -->
# 󰘬                                 

add_newline = true

format = """
╭──$os$username$hostname[](fg:#00fff5) $directory
|
╰──$git_branch$git_status$git_state$git_metrics$docker_context$kubernetes$terraform$c$cpp$python$rust$nodejs$go$java$php$ruby$haskell$zig$swift$kotlin$dotnet$bun$deno$lua$cmake$package$character
"""

########################################
#####---------- Hardware ----------#####
########################################
right_format = """$memory_usage$cmd_duration$time"""

[os]
disabled = false
style = "bg:#00fff5 fg:#0b1c2c"
format = "[$symbol]($style)"

[os.symbols]
Windows = "󰍲 "
Ubuntu = "󰕈 "
SUSE = " "
Raspbian = "󰐿 "
Mint = "󰣭 "
Macos = "󰀵 "
Manjaro = " "
Linux = "󰌽 "
Gentoo = "󰣨 "
Fedora = "󰣛 "
Alpine = " "
Amazon = " "
Android = " "
AOSC = " "
Arch = "󰣇 "
Artix = "󰣇 "
EndeavourOS = " "
CentOS = " "
Debian = "󰣚 "
Redhat = "󱄛 "
RedHatEnterprise = "󱄛 "
Pop = " "

[username]
show_always = true
style_user = "bg:#000000 fg:#ffffff"
style_root = "bg:#000000 fg:#ffffff"
format = "[$user]($style)"

[hostname]
ssh_only = false
style = "bg:#00fff5 fg:#0b1c2c"
format = "[@$hostname]($style)"

[directory]
style = "fg:#e08fff"
format = "[ 󰉋 ](bg:#e08fff fg:#0b1c2c) [ $path ]($style)"
truncation_length = 3
truncation_symbol = "…/"

[directory.substitutions]
"Documents" = "󰈙 "
"Downloads" = "󱑢 "
"Music" = "󰝚 "
"Pictures" = "󰙏 "
"Developer" = "󟤧 "

[git_branch]
symbol = "󰘬"
style = "fg:#00fff5"
format = " [ $symbol $branch ](bg:#e08fff fg:#000000)"

[git_status]
style = "fg:#ffffff"
format = "[[($all_status$ahead_behind )]($style)]($style)"

[git_metrics]
disabled = false
added_style = "fg:#e08fff"
deleted_style = "fg:#e08fff"
format = "[+$added]($added_style)/[-$deleted]($deleted_style) "

#########################################
#####---------- Languages ----------#####
#########################################
[python]
symbol = "󱔎 "
style = "fg:#e08fff"
format = " [ $symbol($virtualenv) ](bg:#e08fff fg:#000000)"

[rust]
symbol = "󱘗 "
style = "fg:#e08fff"
format = " [ $symbol($version) ](bg:#e08fff fg:#000000)"

[nodejs]
symbol = "󰎙 "
style = "fg:#e08fff"
format = " [ $symbol($version) ](bg:#e08fff fg:#000000)"

[golang]
symbol = " "
style = "fg:#e08fff"
format = " [ $symbol($version) ](bg:#e08fff fg:#000000)"

[cpp]
symbol = " "
style = "fg:#e08fff"
format = " [ $symbol($version) ](bg:#e08fff fg:#000000)"

[c]
symbol = " "
style = "fg:#e08fff"
format = " [ $symbol($version) ](bg:#e08fff fg:#000000)"

[lua]
symbol = "󰢱 "
style = "fg:#e08fff"
format = " [ $symbol($version) ](bg:#e08fff fg:#000000)"

#######################################
#####---------- Modules ----------#####
#######################################
[memory_usage]
disabled = false
threshold = 30
style = "fg:#585b70"
symbol = "󰍛 "
format = "[$symbol${ram} ]($style)"

# [battery]
# disabled = true
# full_symbol = "󰁹 "
# charging_symbol = "󰂄 "
# discharging_symbol = "󰂃 "
# format = "[$symbol$percentage]($style) "

# [[battery.display]]
# disabled = true
# threshold = 20
# style = "fg:#ffffff"

[time]
disabled = false
time_format = "%R"
style = "fg:#585b70"
format = "󱑒 $time "

[cmd_duration]
min_time = 500
style = "fg:#585b70"
format = "󱎫 $duration "

#####################################
#####---------- Input ----------#####
#####################################
[character]
success_symbol = " [󰄾 ](fg:#ffffff)"
error_symbol = " [󰅙 ](fg:#ff6666)"
