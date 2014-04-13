# Bukkit Migration Tools

Offers tools and helpers to migrate between breaking changes introduced by different versions of Bukkit/CraftBukkit

## UUIDFetcher

Fetches player UUIDs in bulk.

by evilmidget38 [original post](http://forums.bukkit.org/threads/player-name-uuid-fetcher.250926/)

### Usage

Using UUIDFetcher is fairly simple. First, you need to instantiate a UUIDFetcher with a List of names to retrieve the UUID for.

    UUIDFetcher fetcher = new UUIDFetcher(Arrays.asList("evilmidget38", "mbaxter"));

Once you've created your UUIDFetcher, all that's left is to actually run it.

If you'd like to run your UUIDFetcher on the thread that you're currently on, simply invoke the method "call",
as shown below. Note that if you're currently on the main thread(inside of an EventHandler or scheduled task),
you should not ever do this.

    Map<String, UUID> response = null;
    try {
        response = fetcher.call();
    } catch (Exception e) {
        getLogger().warning("Exception while running UUIDFetcher");
        e.printStacktrace();
    }


## UUIDCache

Offers a cache for player name-UUID mappings that can be used from plugins running on older versions of Bukkit (pre-1.7.5)
which do not yet support player name conversion directly.

by James Crasta [original source](https://github.com/crast/CrastBukkitUtils/blob/master/base/src/main/java/us/crast/bukkituuid/UUIDCache.java)

Please refer to source/JavaDoc for usage.