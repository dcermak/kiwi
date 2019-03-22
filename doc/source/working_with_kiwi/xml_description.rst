The Image Description
=====================

The image description file is a XML file that defines the basic aspects of
the image that will be build by KIWI, for example:

- image type (e.g. QEMU disk image, PXE bootable image, Vagrant box, etc.)
- partition layout
- packages that to be installed on the system
- users to be added

The following sections explain the major elements and attributes of the XML
schema. A complete description of it can be found in :ref:`schema-docs`.


The Image Element
-----------------

The image definition starts with an image tag and requires the schema
format at version 2.0. The attribute name specifies the name of the image
which is also used for the filenames created by KIWI. Because we don’t want
spaces in filenames the name attribute must not have any spaces in its
name.

The following optional attributes can be inserted in the image tag:

displayname

    Allows setup of the boot menu title for the selected boot loader. So you can have suse-SLED-foo as the image name but a different name as the boot display name. Spaces are not allowed in the display name because it causes problems for some boot loaders and kiwi did not take the effort to separate the ones which can display them correctly from the ones which can't 
kiwirevision

    specifies a KIWI git revision number which is known to build a working image from this description. If the KIWI git revision doesn't match the specified value, the process will exit. The currently used git revision can be queried by calling kiwi --version. 
id

    sets an identification number which appears as file /etc/ImageID within the image. 

Inside the image section the following mandatory and optional subelements exists. The simplest image description must define the elements description, preferences, repository and packages (at least one of type="bootstrap").
