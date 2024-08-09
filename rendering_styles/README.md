# Rendering styles

This directory contains rendering style files, which dictate how the map should be rendered.
See [the OsmAnd documentation](https://osmand.net/docs/technical/osmand-file-formats/osmand-rendering-style/) for details on the format of these files.

## Installing modified rendering styles

To test changes to these rendering styles, you can make changes and then copy the modified files into the `Android/data/net.osmand/files/rendering`
directory (or `net.osmand.plus` for OsmAnd plus and `net.osmand.dev` for OsmAnd nightly/beta) on the Android device (these files should be visible through any
file manager, or when browsing files via USB). There might already be files with the same name in that directory - OsmAnd copies the default builtin styles into
that directory whenever you use them or whenever OsmAnd is updated (so any changes you make will last until the next update).

Alternatively, to simplify this install process, you can generate an .osf file using the `build_osf.sh` script, and then open that with OsmAnd to import these
files into the right place automatically (this might ask to overwrite files for
styles that you have used before, which is ok). You can run the script without
arguments to generate an osf file with *all* rendering styles:

    $ ./build_osf.sh
      adding: LightRS.render.xml (deflated 87%)
      adding: Topo-map-assimilation.render.xml (deflated 87%)
      [ ... snip more files ...]
      adding: weather.addon.render.xml (deflated 77%)
      adding: items.json (deflated 89%)
    Created RenderingStyles.osf

Alternatively, pass filenames to include only those files:


    $ ./build_osf.sh  routes.addon.render.xml default.render.xml
      adding: routes.addon.render.xml (deflated 89%)
      adding: default.render.xml (deflated 87%)
      adding: items.json (deflated 53%)
    Created RenderingStyles.osf

In both cases, such changes last until the next update of OsmAnd, then they are overwritten with the default version again.

This script uses POSIX sh, the `jq`, `zip` and `sponge` commands, so it should run on Linux and probably MacOS.
