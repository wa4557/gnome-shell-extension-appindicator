# AppIndicator support for GNOME Shell
This extension integrates AppIndicators, which are quite popular since the introduction of ubuntu unity, into the gnome shell.

It's based on patches made by Giovanni Campagna: https://bugzilla.gnome.org/show_bug.cgi?id=652122

## Features
* Show indicator icons in the message tray or in the panel (can be configured even per indicator!)
* Reveal indicator menus upon click.

## Missing features
* Tooltips: Not implemented in `libappindicator` and I've yet to see any indicator using it (KDE ones maybe?). They're likely to return (like implemented in the original patch) as soon as there is proven (and testable) real world usage.
* Oversized icons like the ones used by `indicator-multiload` are unsupported. They will be shrunk to normal size.

## Buggy features
* Icon pixmaps are untested and will probably not work correctly. If we can't find any real world usage they will be removed in near future.
* Ayatana labels are supported in the panel only.
* Re-enabling the extension after you disabled it doesn't work as of now - you need to restart the shell.
* The whole thing eats a bunch of memory. There is no evidence for memory leaks (yet) but the garbage collector seems to have severe problems dealing with changing icons.
* `nm-applet` is broken: https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/965895

## TODO
* Move everything to GDBus - gjs master already removed the legacy DBus bindings.
* Add Localization.