shredisfs - a redis based filesystem.

Based on http://www.steve.org.uk/Software/redisfs/ by Steve Kemp, with some modifications.

Steve's original managed around 250k per second for writes on my test machine, this version does about 15MB a second writes. (Basic single CPU debian squeeze vm on Fusion 3).

More optimisations could be had by forcing the FUSE driver to use a larger block size, at present it receives blocks at 4k each, which isn't good for limiting the number of operations to redis.

The main optimisation was command bundling (issuing many commands to redis at once) and changing the mech for data copy to use the APPEND operation, rather than GET, memcpy, SET.

There is still a bit more optimisation that could be done in the connection check and find_inode features, I have changed the connection check so it will only PING redis after 2 seconds from the last PING.
