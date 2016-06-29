# systemd-units
Here are some of my systemd units.

- **mysql.service.d/override.conf** - Used to modify (override) the shipped unit with my own setting of max. number of open files

- **cluebringer.service** - Unit for postfix policyd v2.0 (Cluebringer). It is a forking service, which requires creating a subdir in /run and does change UID on its own

- **dccifd.service** - Unit for DCC (Distributes Checksum Clearinghouse) email reputation daemon. Written in the same style as cluebringer unit, but DCC writes its pidfile in nonstandard way, so we leave it up to systemd to guess the main pid.

- **yaa.service** - Unit for Yaa (Yet Another Autoresponder). Yaa is written in Perl, utilizing module Net::Server. When configured not to fork, it works perfectly with systemd in "simple" mode.

- **parse_sasl.service**, **parse_sagator.service** - These are just simple perl script analyzing logfiles using File::Tail. They don't have any daemon support, so work nicely in systemd "simple" mode. We redirect stdout to systemd's journal to be able to read it (you must unbuffer stdout in perl - see more in my blog post).

More details about how to write systemd units is in my blog post: https://www.marki-online.net/myblog/tips-tricks-for-systemd/

