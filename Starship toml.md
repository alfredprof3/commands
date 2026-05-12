# Setups
# format = "$directory$git_branch$character"
format = """
$os\
$directory\

$kubernetes\
$hg_branch\
$docker_context\

$fill\
$git_branch\
$git_status\
$git_commit\
$jobs\
$status\
$container\
$shell\
$time\
$line_break\
$character"""
add_newline = true # Disable the blank line at the start of the prompt


[os]
format = "[](fg:#6791C9 bg:none)[ ](fg:#252525 bg:#6791C9)[](fg:#6791C9 bg:#8994fa)"
disabled = false

[directory]
format = "[  ](fg:#252525 bg:#8994fa)[](fg:#8994fa bg:#252525)[█](fg:#252525 bg:none)[$path]($style)[](fg:#232526 bg:none)"
style = "fg:#E8E3E3 bg:#252525 bold"
truncation_length = 2
truncate_to_repo = true
read_only = "  "
home_symbol = " 󰋜  "

[directory.substitutions]
"Documents" = "  "
"Downloads" = "  "
"Music" = "  "
"Pictures" = "  "

# Prompt symbols
[character]
success_symbol = "[ 🞈 ](#6791C9 bold)"
error_symbol = "[ 🞈 ](#B66467 bold)"

[line_break]
disabled = false
