# desktop-widget

At `~/.config/conky/conky.conf`
```
-- Conky, a system monitor https://github.com/brndnmtthws/conky
--
-- This configuration file is Lua code. You can write code in here, and it will
-- execute when Conky loads. You can use it to generate your own advanced
-- configurations.
--
-- Try this (remove the `--`):
--
--   print("Loading Conky config")
--
-- For more on Lua, see:
-- https://www.lua.org/pil/contents.html

conky.config = {
    alignment = 'top_left',
    background = false,
    border_width = 1,
    cpu_avg_samples = 2,
    default_color = 'white',
    default_outline_color = 'white',
    default_shade_color = 'white',
    double_buffer = true,
    draw_borders = false,
    draw_graph_borders = true,
    draw_outline = false,
    draw_shades = false,
    extra_newline = false,
    font = 'DejaVu Sans Mono:size=12',
    gap_x = 60,
    gap_y = 60,
    minimum_height = 5,
    minimum_width = 5,
    maximum_width = 400,
    net_avg_samples = 2,
    no_buffers = true,
    out_to_console = false,
    out_to_ncurses = false,
    out_to_stderr = false,
    out_to_x = true,
    own_window = true,
    own_window_class = 'Conky',
    own_window_type = 'desktop',
    show_graph_range = false,
    show_graph_scale = false,
    stippled_borders = 0,
    update_interval = 1.0,
    uppercase = false,
    use_spacer = 'none',
    use_xft = true,
}

conky.text = [[
${color grey}Info:$color $sysname $nodename
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar 6 /}

$hr
${color grey}NETWORK (${addr enp130s0}) ${hr 2}
${color grey}Speed:${color} ↑ ${upspeed enp130s0}/s ${alignr}↓ ${downspeed enp130s0}/s
${upspeedgraph enp130s0 25,140 85c2ff b2cfff} ${alignr}${downspeedgraph enp130s0 25,140 85c2ff b2cfff}
${color grey}Today:${color} ${execi 300 vnstat -i enp130s0 -d | grep "$(date +%Y-%m-%d)" | awk '{print "↓ " $2 " " $3 "  |  ↑ " $5 " " $6 "  |"}'}
Total:   ${execi 300 vnstat -i enp130s0 -d | grep "$(date +%Y-%m-%d)" | awk '{print $8 " " $9}'}

${color grey}NVIDIA GPU ${hr 2}
${color grey}GPU:$color ${execi 5 nvidia-smi --query-gpu=name --format=csv,noheader,nounits | head -n 1}
${color grey}Temp:$color ${execi 2 nvidia-smi --query-gpu=temperature.gpu --format=csv,noheader,nounits | head -n 1}°C ${alignr}${color grey}Fan:$color ${execi 2 nvidia-smi --query-gpu=fan.speed --format=csv,noheader,nounits | head -n 1}%
${color grey}Usage:$color ${execi 2 nvidia-smi --query-gpu=utilization.gpu --format=csv,noheader,nounits | head -n 1}% ${execibar 2 nvidia-smi --query-gpu=utilization.gpu --format=csv,noheader,nounits | head -n 1}
${color grey}VRAM:$color ${execi 2 nvidia-smi --query-gpu=memory.used,memory.total --format=csv,noheader,nounits | head -n 1 | awk -F', ' '{print $1 " MiB / " $2 " MiB"}'}
${color grey}Power:$color ${execi 2 nvidia-smi --query-gpu=power.draw,power.limit --format=csv,noheader,nounits | head -n 1 | awk -F', ' '{print $1 " W / " $2 " W"}'}
${color grey}Clocks:$color G ${execi 5 nvidia-smi --query-gpu=clocks.gr --format=csv,noheader,nounits | head -n 1} MHz  M ${execi 5 nvidia-smi --query-gpu=clocks.mem --format=csv,noheader,nounits | head -n 1} MHz

${color grey}TOP PROCESSES ${hr 2}
${color grey}Name              PID     CPU%   MEM%
${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
]]
```


