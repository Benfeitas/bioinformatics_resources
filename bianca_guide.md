# Bianca guide

Refer to the [official guide here](https://www.uppmax.uu.se/support/user-guides/bianca-user-guide/). You need to set up 2-factor authentication as [indicated here](https://www.uppmax.uu.se/support/user-guides/bianca-user-guide/).

## Connection
**Connection Option A:**
1. Set up your university VPN;
2. `ssh` to bianca
	`ssh -A <your username>-<project id>@bianca.uppmax.uu.se`
3. Use the same password as for Rackham, followed by the 2-factor authentication code
	`<rackham-password><2-factor-auth-code>`
4. Insert again your password without 2-factor authentication code

**Connection Option B:**
1. `ssh` into rackham
	`ssh -Y yourusername@rackham.uppmax.uu.se`
2. `ssh` to bianca
	`ssh -A <your username>-<project id>@bianca.uppmax.uu.se`
3. Use the same password as for Rackham, followed by the 2-factor authentication code
	`<rackham-password><2-factor-auth-code>`
4. Insert again your password without 2-factor authentication code

## File transfer
1. ssh into rackham
2. `ssh <yourusername>@transit.uppmax.uu.se`
3. `mount_wharf <project id> <path>`

## Install Nextflow
As `bianca` is secure, no direct download is available, so Nextflow and nf-core pipelines will have to be installed and updated manually. This guide was adapted [from Sarek's guide](https://github.com/SciLifeLab/Sarek/blob/master/docs/INSTALL_BIANCA.md#install-nextflow).

```bash
# Connect to rackham
> ssh -AX [USER]@rackham.uppmax.uu.se

# Download the all Nextflow bundle
> wget https://github.com/nextflow-io/nextflow/releases/download/v[xx.yy.zz]/nextflow-[xx.yy.zz]-all

# Send to bianca (here using sftp)
# For FileZilla follow the bianca user guide
> sftp [USER]-[PROJECT]@bianca-sftp.uppmax.uu.se:[USER]-[PROJECT]
> put nextflow-[xx.yy.zz]-all

# Exit sftp
> exit

# Connect to bianca
> ssh -A [USER]-[PROJECT]@bianca.uppmax.uu.se

# Go to your project
> cd /castor/project/proj_nobackup

# Make directory for Nextflow
> mkdir tools
> mkdir tools/nextflow

# Move Nextflow from wharf to its directory
> mv /castor/project/proj_nobackup/wharf/[USER]/[USER]-[PROJECT]/nextflow-[xx.yy.zz]-all /castor/project/proj_nobackup/tools/nextflow

# Establish permission
> chmod a+x /castor/project/proj_nobackup/tools/nextflow/nextflow-[xx.yy.zz]-all

# If you want other people to use it
# Be sure that your group has rights to the directory as well

> chown -R .[PROJECT] /castor/project/proj_nobackup/tools/nextflow/nextflow-[xx.yy.zz]-all

# Make a link to it
> ln -s /castor/project/proj_nobackup/tools/nextflow/nextflow-[xx.yy.zz]-all /castor/project/proj_nobackup/tools/nextflow/nextflow

# And everytime you're launching Nextflow, don't forget to export the following ENV variables
# Or add them to your .bashrc file
> export NXF_HOME=/castor/project/proj/nobackup/tools/nextflow/
> export PATH=${NXF_HOME}:${PATH}
> export NXF_TEMP=$SNIC_TMP
> export NXF_LAUNCHER=$SNIC_TMP
```

## Installinf NF-Core pipelines
You can either download pipelines on your computer or on `rackham`, make an archive, and send it to `bianca` using `FileZilla` or `sftp` given your preferences.

```bash
# Connect to rackham
> ssh -AX [USER]@rackham.uppmax.uu.se
# Or just open a terminal

# Install nf-core
> conda install nf-core
# or install the devel version
> pip install --upgrade --force-reinstall git+https://github.com/nf-core/tools.git@dev

# Install a pipeline.
> nf-core download rnaseq -r 3.0 --singularity

# Send the tar to bianca (here using sftp)
# For FileZilla follow the bianca user guide
> sftp [USER]-[PROJECT]@bianca-sftp.uppmax.uu.se:[USER]-[PROJECT]
> put nf-core-rnaseq-3.0.tar.gz
> exit

# The archive will be in the wharf folder in your user home on your bianca project

# Connect to bianca
> ssh -A [USER]-[PROJECT]@bianca.uppmax.uu.se

# Go to your project
> cd /castor/project/proj_nobackup

# Make and go into a nf-core directory (where you will store all pipeline versions)
> mkdir nf-core-rnaseq-3
> cd nf-core-rnaseq-3

# Copy the tar from wharf to the project
> cp /castor/project/proj_nobackup/wharf/[USER]/[USER]-[PROJECT]/nf-core-rnaseq-3.0.tar.gz /castor/project/proj_nobackup/nf-core-rnaseq-3

# extract the pipeline. Also remember to extract the containers you uploaded.
> tar xvzf nf-core-rnaseq-3.0.tar.gz
```

Move the singularity images to a common dir in the project, to be re-used
```bash
cd /castor/project/proj/nobackup/tools/
mv /castor/project/proj/nobackup/tools/singularity-images .
```

Set a common var pointing to this dir
```bash
## add to .bashrc
export NXF_SINGULARITY_CACHEDIR=/castor/project/proj/nobackup/tools/singularity-images/
```