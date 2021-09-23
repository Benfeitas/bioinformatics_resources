# SFTP cheat sheet

To connect to bianca:
1. Log into rackham
2. `sftp -q <username>-<projid>@bianca-sftp.uppmax.uu.se`


- `?` check help
- `cd` change remote dir
- `lcd` change local dir
- `pwd` check remote pwd
- `lpwd` check local pwd
- `ls` list remote files
- `lls` list local files
- `put local_file.txt` upload local file
- `mput *.xls` upload multiple local files
- `get my_file.txt` download remote file
- `mget *.xls` download multiple remote files
- `mkdir` create remote dir
- `lmkdir` create local dir
- `rm my_file.xls` remove remote file
- `rmdir my_dir` remove remote dir
- `!` move to local shell
- `exit` leave sftp

