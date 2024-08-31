# Custom Alfred WezTerm Script

AppleScript for [WezTerm](https://wezfurlong.org/wezterm/index.html) [Alfred](https://www.alfredapp.com/) integration. Inspired by [Vitorgalvao's script for iTerm](https://github.com/vitorgalvao/custom-alfred-iterm-scripts).

## Preview
![Aug-31-2024 14-38-20](https://github.com/user-attachments/assets/bf914ff0-8df2-45a4-ba73-36d64ef4fd56)


## Setup

1. Copy the script to your clipboard (see below).
2. Open Alfred Preferences (call Alfred and press ⌘,).
3. Navigate to Features → Terminal → Custom.
4. Set Application to Custom.
5. Select the text in the box.
6. Paste the script.
7. Launch Alfred.
8. Start with a `>` and type your command.
9. Press Enter.
10. It will open WezTerm and execute your command in a new tab.

## Script

```shell
on alfred_script(query)
	tell application "wezterm" to activate
	set paneId to do shell script "/Applications/WezTerm.app/Contents/MacOS/wezterm cli spawn"
	set commandList to paragraphs of query
	repeat with command in commandList
		do shell script "echo " & command & " | /Applications/WezTerm.app/Contents/MacOS/wezterm cli send-text --no-paste --pane-id " & paneId
	end repeat
end alfred_script
```

