if ENABLE_DEBUG
DEBUG_OPTS = -g -DMTN_DEBUG
endif
if ENABLE_MTNFS
sbin_PROGRAMS = mtnd mtnfs
mtnfs_SOURCES = mtnfs.c common.c
mtnfs_CFLAGS  = -DMODULE_NAME=\"mtnfs\" -Wall $(DEBUG_OPTS) $(FUSE_CFLAGS)
mtnfs_LDADD   = libmtn.a -lfuse $(FUSE_LDFLAGS)
else
sbin_PROGRAMS = mtnd
endif
bin_PROGRAMS     = mtnexec mtnfile
noinst_LIBRARIES = libmtn.a
libmtn_a_SOURCES = libmtn.c
mtnd_SOURCES     = mtnd.c mtnd_child.c common.c
mtnexec_SOURCES  = mtnexec.c common.c
mtnfile_SOURCES  = mtnfile.c common.c
libmtn_a_CFLAGS  = -Wall $(DEBUG_OPTS)
mtnd_CFLAGS      = -DMODULE_NAME=\"mtnd\" -Wall $(DEBUG_OPTS)
mtnexec_CFLAGS   = -DMODULE_NAME=\"mtnexec\" -Wall $(DEBUG_OPTS)
mtnfile_CFLAGS   = -DMODULE_NAME=\"mtnfile\" -Wall $(DEBUG_OPTS)
mtnd_LDADD       = libmtn.a
mtnexec_LDADD    = libmtn.a
mtnfile_LDADD    = libmtn.a -lreadline

test: mtnd mtnexec mtnfile
	./mtntest ./test
