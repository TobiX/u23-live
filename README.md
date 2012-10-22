CCCC U23 2012 Xfce Desktop
==========================

This is a live-build configuration for a simple Xfce-based system with our
STM32-Toolchain (<https://github.com/cccc/STM32-Toolchain>) preinstalled in
/opt/stm32.

This repository does not contain the (quite hacky) stm32-toolchain*.deb
packages, but they can easily be added via git-annex:

	apt-get install live-build git-annex
	mkdir u32-live
	cd u23-live
	lb config --config https://github.com/TobiX/u23-live
	git annex init
	# Get the correct one from http://23.gs/u23/ (see filename in
	# config/packages.chroot)
	git annex addurl http://23.gs/u23/stm32-toolchain_2_i386.deb \
		http://23.gs/u23/stm32-toolchain-extras_2_all.deb
	# Since this should have relinked config/packages.chroot/*.deb...
	git rm -f *.deb
	sudo lb build

Now get a coffee and some time later you should have a nice ISO to write to a
CD/DVD/USB device.
