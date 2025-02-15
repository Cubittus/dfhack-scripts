light-aquifers-only
===================

.. dfhack-tool::
    :summary: Change heavy and varied aquifers to light aquifers.
    :tags: unavailable embark fort armok map

This script behaves differently depending on whether it's called pre-embark or
post-embark. Pre-embark, it changes all aquifers in the world to light ones,
while post-embark it only modifies the map tiles, leaving the rest of the world
unchanged.

Usage
-----

::

    light-aquifers-only

If you don't ever want to have to deal with heavy aquifers, you can add the
``light-aquifers-only`` command to your :file:`dfhack-config/init/onMapLoad.init`
file.

Technical details
-----------------

When run pre-embark, this script changes the drainage of all world tiles that
would generate Heavy aquifers into a value that results in Light aquifers
instead, based on logic revealed by ToadyOne in a FotF answer:
http://www.bay12forums.com/smf/index.php?topic=169696.msg8099138#msg8099138

Basically, the drainage is used as an "RNG" to cause an aquifer to be heavy
about 5% of the time. The script shifts the matching numbers to a neighboring
one, which does not result in any change of the biome.

When run post-embark, this script simply clears the flags that mark aquifer
tiles as heavy, converting them to light.
