```json
{

"$schema": "https://github.com/fastfetch-cli/fastfetch/raw/dev/doc/json_schema.json",

"logo": {

"padding": {

"top": 2

}

},

"modules": [

"break",

{

"type": "datetime",

"key": "├󰥔 DATE/TIME",

"keyColor": "green"

},

{

"type": "title",

"key": "├ HOST",

"keyColor": "green"

},

{

"type": "chassis",

"key": "│├󰇅 CHASSIS",

"keyColor": "green"

},
				
{

"type": "board",

"key": "││├ MOBO",

"keyColor": "green"

},

{

"type": "bios",

"key": "│││├ BIOS",

"keyColor": "green"

},

{

"type": "cpu",

"showPeCoreCount": true,

"temp": true,

"key": "│││├ CPU",

"keyColor": "green"

},

{

"type": "physicaldisk",

"key": "│││├ DISK",

"keyColor": "green"

},

  

{

"type": "memory",

"key": "│││├ MEM",

"keyColor": "green"

},

{

"type": "swap",

"key": "││││├󰓡 SWAP",

"keyColor": "green"

},

{

"type": "gpu",

"key": "│││├󰍹 GPU",

"keyColor": "green"

},

{

"type": "display",

"key": "││││├󰍹 DISPLAYS",

"keyColor": "green"

},

{

"type": "opengl",

"key": "││││├󰍹 GL",

"keyColor": "green"

},

{

"type": "opencl",

"key": "││││├󰍹 CL",

"keyColor": "green"

},

{

"type": "kernel",

"key": "│├ KERNEL",

"keyColor": "yellow"

},

{

"type": "uptime",

"key": "││├󰥔 UPTIME",

"keyColor": "yellow"

},

{

"type": "os",

"key": "││├ DISTRO",

"keyColor": "yellow"

},

{

"type": "packages",

"key": "│││├󰏖 PACKAGES",

"keyColor": "yellow"

},

{

"type": "terminal",

"key": "│││├ terminal",

"keyColor": "yellow"

},

{

"type": "terminaltheme",

"key": "││││├󰉼 THEME",

"keyColor": "yellow"

},

{

"type": "terminalfont",

"key": "││││├󰛖 FONT",

"keyColor": "yellow"

},

{

"type": "shell",

"key": "││││├ SHELL",

"keyColor": "yellow"

},

{

"type": "editor",

"key": "│││├ EDITOR",

"keyColor": "yellow"

},

{

"type": "lm",

"key": "│││├󰟵 LM",

"keyColor": "magenta"

},

{

"type": "de",

"key": "│││├󰧨 DE",

"keyColor": "magenta"

},

{

"type": "theme",

"key": "│││││├󰉼 THEME",

"keyColor": "magenta"

},

{

"type": "icons",

"key": "│││││├ ICONS",

"keyColor": "magenta"

},

{

"type": "cursor",

"key": "│││││├󰇀 CURSOR",

"keyColor": "magenta"

},

{

"type": "font",

"key": "│││││├ FONT",

"keyColor": "magenta"

},

{

"type": "wm",

"key": "││││├ WM",

"keyColor": "magenta"

},

{

"type": "wmtheme",

"key": "│││││├󰉼 WM THEME",

"keyColor": "magenta"

},

{

"type": "battery",

"temp": true

},

{

"type": "custom",

"format": "\u001b[90m \u001b[31m \u001b[32m \u001b[33m \u001b[34m \u001b[35m \u001b[36m \u001b[37m \u001b[38m \u001b[39m \u001b[39m  \u001b[38m \u001b[37m \u001b[36m \u001b[35m \u001b[34m \u001b[33m \u001b[32m \u001b[31m \u001b[90m "

},

"break"

]

}
```