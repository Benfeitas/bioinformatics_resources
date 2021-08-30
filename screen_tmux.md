# screen / tmux

## tmux
- `tmux new -s [session_name]`		#start named session
- `tmux a -t [session_name]`		#attach session
- `CTRL+b` and `d` #detach session 
- `tmux detach`		#detach session
- `tmux ls`		#list sessions
- `exit` or `CTRL+d`			#exit tmux
- `CRTL+b+"`		#split screen horizontally
- `CTRL+b+%`		#split screen vertically
- `CTRL+b+o`		#toggle panes


## Using screen
To use screen:
1. `ssh` to uppmax
2. `screen -S some_screen_name`
3. start jobs
4. detach with `Ctrl + A + D` or `screen -r -d some_screen_name`
5. kill with `Ctrl + A + x`

- `screen -S [name]`        #create a screen named [name]  
- `screen -ls`            #list all screens  
- `screen -r [name]`        #attach to screen  
- `screen -r -d [name]`        #to for attach to screen  

