shredisfs - a redis based filesystem.

Based on http://www.steve.org.uk/Software/redisfs/ by Steve Kemp, with some modifications.

Steve's original managed around 250k per second for writes on my test machine, this version does about 15MB a second writes. (Basic single CPU debian squeeze vm on Fusion 3).

The main optimisation was command bundling (issuing many commands to redis at once) and changing the mech for data copy to use the APPEND operation, rather than GET, memcpy, SET.

Read speed on the test machine here now is around 180MB/sec, after changing to GETRANGE to grab the file contents from Redis, up from about 250kb/sec or so. 

