##############################################################################
# automates the creation of python package structures
#
# usage: python pypkginit pkg_title author_name author_email pkg_version
#
# author: Damon Swayn
# date: 1/2/13
# license: MIT license
#############################################################################

import sys
import os
from time import gmtime, strftime

title = str(sys.argv[1])
author = str(sys.argv[2])
email = str(sys.argv[3])
version = str(sys.argv[4])

if not os.path.exists(title):
    os.makedirs(title) #make directory
else:
    print "directory already exists, please rename."
    sys.exit(-1)

os.chdir(title) #move into new directory

#we can now assume that the following can be created without clashes
#taken from https://guide.python-distribute.org/creation.html
os.makedirs("bin")
os.makedirs("docs")
os.makedirs(title)

changes = open("CHANGES.txt", 'w+')
license = open("LICENSE.txt", 'w+')
manifest = open("MANIFEST.in", 'w+')
readme = open("README.txt", 'w+')
setup = open("setup.py", 'w+')

changes.write("v" + version + ", " + strftime("%Y-%m-%d", gmtime()) + " -- Initial release.")
changes.close()

license.close()

manifest.write("include *.txt\nrecursive-include docs *.txt")
manifest.close()

readme.write("please update your readme file.")
readme.close()

setup.write("from distutils.core import setup\n\nsetup(\n\tname='" + title +"',\n\tversion='" + version + "',\n\tauthor='" + author + "',\n\tauthor_email='" + email + "',\n\tpackages=['" + title + "'],\n\tscripts=[],\n\turl='enter_url_here',\n\tlicense='LICENSE.txt',\n\tdescription='enter description here.'\n\tlong_description=open('README.txt').read(),\n\tinstall_requires=[],\n)")
setup.close()

os.chdir(title)
init = open("__init__.py", '+w')
init.close()

os.makedirs(title + "_tests")
