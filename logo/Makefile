# This Makefile creates the logo in different formats based on the svg version
#  in svg/coderetreat-logo.svg. A Makefile specifies how a specific file should
#  be created. If that file needs a different file to work on,  e.g. like the
#  jpg files that need the png files, Make will create the png's first using
#  the recipe specified for them.
#
# To create the images, make, imagemagick and inkscape need to be installed.
# On Mac, make should come with XCode (https://developer.apple.com/xcode/),
#  imagemagick can be installed using brew (`brew install imagemagick`)
#  and inkscape is available as a package from https://inkscape.org/
#
# On Linux, all three applications should be available in your package-manager
#  where `make` comes with `build-essentials` on Ubuntu & `base-devel` on Arch
#
# If you want to update all rasterized versions, issuing `make all` should
#  re-create all files. If Make reports `make: Nothing to be done for 'all'.`,
#  that means the source file (the svg) hasn't changed and thus Make does not
#  need to recreate the rasterized versions.
#
# If you want to force re-creation, issue `make clean`, which will delete all
#  rasterized versions and then will force `make all` to re-create them.

# Create all derived formats using the recipes below
all: clean pdf png

# clean is .PHONY because it doesn't create a file.
#  it will delete all derived files. Usually you won't need this.
#  (https://www.gnu.org/software/make/manual/html_node/Phony-Targets.html)
.PHONY: clean
clean:
	-mkdir pdf
	-mkdir png
	-rm pdf/*.pdf
	-rm png/*.png


pdf: pdf/logo.pdf pdf/logo-with-slogan.pdf
png: png/logo.png png/logo-160x.png png/logo-300x.png png/logo-with-slogan.png png/logo-with-slogan-160x.png png/logo-with-slogan-300x.png

# Create a PDF version of the logo
#
# A 'target' can be read as
# > In order to create pdf/coderetreat-logo.pdf
# > Issue the following command that requires svg/coderetreat-logo.svg to be present
pdf/%.pdf: svg/%.svg
	inkscape -z -A $@ $<

# Create the logo as a PNG at different resolutions (300dpi, 160x160px, 300x300px)
png/%.png: svg/%.svg
	inkscape -z -e $@ -d 300 $<

png/%-160x.png: svg/%.svg
	inkscape -z -e $@ -w 160 $<

png/%-300x.png: svg/%.svg
	inkscape -z -e $@ -w 300 $<
