# Copyright (C) 2011-2015 Aratelia Limited - Juan A. Rubio
#
# This file is part of Tizonia
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

ACLOCAL_AMFLAGS = -I m4

TARBALL_NAME = MechanicalSoup
MODULE_NAME = mechanicalsoup

#python_PYTHON =

.PHONY: sdist
sdist:
	cd $(MODULE_NAME) && python setup.py sdist

.PHONY: debs
debs: sdist
	rm -rf build && mkdir build
	cp $(MODULE_NAME)/dist/$(TARBALL_NAME)-*.tar.gz build
	cd build && py2dsc -m 'Juan A. Rubio <juan.rubio@aratelia.com>' $(TARBALL_NAME)-*.tar.gz
	PROJ_BUILD_DIR=$$(echo build/*.tar.gz | grep -Po '$(TARBALL_NAME)-(\d.){2}\d' | awk '{ print tolower($$0) }') ; \
	echo $$PROJ_BUILD_DIR; \
	cp -f debian/copyright debian/control debian/changelog build/deb_dist/$$PROJ_BUILD_DIR/debian ; \
	cd build/deb_dist/$$PROJ_BUILD_DIR && debuild -i -us -uc -b --lintian-opts --profile debian

.PHONY: install-exec-local
install-exec-local:
	sudo dpkg -i build/deb_dist/*.deb

.PHONY: uninstall-local
uninstall-local:
	sudo apt-get -y remove python-$(MODULE_NAME) && sudo apt-get -y autoremove

clean-local: clean-local-check
.PHONY: clean-local-check
clean-local-check:
	-rm -rf build

.DEFAULT_GOAL = debs
