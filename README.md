# The Great Vanderbilt Hackathon of March, 2025

## Use the Container

 * Get the container
 * Get into a directory of your project
 * Run the container

Example:

```bash
docker pull  public.ecr.aws/h0v7t0b7/vandyhack/adviser-cli:latest
cd ${your_project_workdir}
docker run \
    --hostname=vandyhack  \
    --platform linux/arm64/v8  \
    -v $PWD:/app/homedir  -it \
    public.ecr.aws/h0v7t0b7/vandyhack/adviser-cli:latest
```

Once you're in the container, you will see that you're in `/app/homedir` which is the
same directory you started the container from. So if you were in your project directory
when you did your `docker run` all your project files will be there and available.

Any edits or changes you make to the files will be reflected in the Adviser environment
automatically. So feel free to make changes using your IDE or whatever.

Login and do a cluster list.

```bash
# here, use vandyhack@adviser.sh username with the password we provide!
adviser login
Enter your email: vandyhack@adviser.sh
Enter your password:
I 04-02 21:54:47 login.py:71] Successfully logged in.

# next up, let's be sure we can see clusters
adviser cluster list
ID  CLUSTER NAME        STATUS   CLOUD  INSTANCE_TYPE
25  adviser-cluster-25  READY    aws    t2.medium
26  adviser-cluster-26  READY    aws    t2.medium
40  adviser-cluster-40  PENDING  aws    t2.medium

# next up, let's create a cluster for your own personal use!
# --setup can include complex commands like apt installations,
# or whatever prerequisites you'll need on the cluster
adviser cluster create --setup="#whatever cluster setup you need"

# notice what the cluster is named. Say its name is "adviser-cluster-99"
# so your cluster ID is 99.
adviser run  --cluster 99  "du -sm */"

# you can run whatever command on the cluster you want, like your
# own project simulations or jobs.
adviser run  --cluster 99  "python my_project_main.py"
```

## Download the CLI

 * [Windows](...)
 * [Linux](...)
 * [MacOS](...)

