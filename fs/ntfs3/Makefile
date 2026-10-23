# SPDX-License-Identifier: GPL-2.0
#
# Makefile for the ntfs3 filesystem support.
#

# to check robot warnings
# -Wunused-but-set-variable/-Wold-style-declaration are GCC-only (this driver
# normally builds with GCC via DKMS); clang's -Werror,-Wunknown-warning-option
# turns the mere presence of an unrecognized flag into a hard error.
ccflags-y += -Wint-to-pointer-cast

obj-$(CONFIG_NTFS3_FS) += ntfs3.o

ntfs3-y :=	attrib.o \
		attrlist.o \
		bitfunc.o \
		bitmap.o \
		dir.o \
		fsntfs.o \
		frecord.o \
		file.o \
		fslog.o \
		inode.o \
		index.o \
		lznt.o \
		namei.o \
		record.o \
		run.o \
		super.o \
		upcase.o \
		xattr.o

ntfs3-$(CONFIG_NTFS3_LZX_XPRESS) += $(addprefix lib/,\
		decompress_common.o \
		lzx_decompress.o \
		xpress_decompress.o \
		)

ccflags-$(CONFIG_NTFS3_LZX_XPRESS) += -DCONFIG_NTFS3_LZX_XPRESS
ccflags-$(CONFIG_NTFS3_FS_POSIX_ACL) += -DCONFIG_NTFS3_FS_POSIX_ACL

all:
	make -C /lib/modules/$(KVERSION)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(KVERSION)/build M=$(PWD) clean