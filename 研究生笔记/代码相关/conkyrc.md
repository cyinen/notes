
我的配置文件

```bash
conky.config = {

alignment = 'top_right',

background = false,

border_width = 1,

cpu_avg_samples = 2,

net_avg_samples = 2,

use_xft = true,

-- Xft font when Xft is enabled

font = 'Sans:size=10',

-- Text alpha when using Xft

xftalpha = 0.8,

default_color = 'black',

default_outline_color = 'white',

default_shade_color = 'white',

draw_borders = false,

draw_graph_borders = true,

draw_outline = false,

draw_shades = false,

  

gap_x = 15,

gap_y = 15,

minimum_height = 5,

minimum_width = 5,

no_buffers = true,

out_to_console = false,

out_to_stderr = false,

extra_newline = false,

  

double_buffer = true,

-- Create own window instead of using desktop (required in nautilus)

own_window = true,

own_window_class = 'Conky',

own_window_argb_visual = true,

own_window_transparent = true,

own_window_hints = 'undecorated,below,sticky,skip_taskbar,skip_pager',

own_window_type = 'desktop',

  

stippled_borders = 0,

update_interval = 1.0,

uppercase = false,

use_spacer = 'none',

show_graph_scale = false,

show_graph_range = false

}

  

conky.text = [[

  

${color #c3e0d2}${font LCD:style=Bold:pixelsize=40}${alignc}${time %I:%M:%S}

${font LCD:style=Bold:pixelsize=20}${time %Y年%b%d日 星期%a}${alignc}

${font WenQuanYi Zen Hei:pixelsize=14}

${color #c3e0d2}BASIC ${hr 1}${color}

${color #f0f7f4}姓名: $alignr$nodename

${color #f0f7f4}邮箱: ${color #98c1c7}$alignr cyinen@qq.com

  

${color #c3e0d2}SYSTEM ${hr 1}${color}

${color #f0f7f4}内核: ${color #98c1c7}$alignr$kernel

${color #f0f7f4}已开机: ${color #98c1c7}$alignr$uptime

  

${color #c3e0d2}CPU ${hr 1}${color}

${color #f0f7f4}CPU: ${alignr}${freq dyn} MHz

${color #f0f7f4}CPU温度: ${alignr}${acpitemp}°C

${cpubar 4 cpu0}

Ram ${alignr}$mem / $memmax ($memperc%)

${membar 4}

swap ${alignr}$swap / $swapmax ($swapperc%)

${swapbar 4}

Highest CPU $alignr CPU% MEM%

${top name 1}$alignr${top cpu 1} ${top mem 1}

${top name 2}$alignr${top cpu 2} ${top mem 2}

${top name 3}$alignr${top cpu 3} ${top mem 3}

]]
```