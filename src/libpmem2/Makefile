# SPDX-License-Identifier: BSD-3-Clause
# Copyright 2019-2021, Intel Corporation

#
# src/libpmem2/Makefile -- Makefile for libpmem2
#

include ../common.inc

LIBRARY_NAME = pmem2
LIBRARY_SO_VERSION = 1
LIBRARY_VERSION = 0.0
SOURCE =\
	libpmem2.c\
	badblocks.c\
	badblocks_$(OS_DIMM).c\
	config.c\
	deep_flush.c\
	errormsg.c\
	map.c\
	map_posix.c\
	mcsafe_ops_posix.c\
	memops_generic.c\
	persist.c\
	persist_posix.c\
	pmem2_utils.c\
	usc_$(OS_DIMM).c\
	source.c\
	source_posix.c\
	vm_reservation.c\
	vm_reservation_posix.c

ifeq ($(OS_KERNEL_NAME),Linux)
SOURCE +=\
	auto_flush_linux.c\
	deep_flush_linux.c\
	extent_linux.c\
	pmem2_utils_linux.c\
	pmem2_utils_$(OS_DIMM).c
else
SOURCE +=\
	auto_flush_none.c\
	deep_flush_other.c\
	extent_none.c\
	pmem2_utils_other.c
endif

ifeq ($(OS_DIMM),ndctl)
SOURCE +=\
	region_namespace_ndctl.c\
	numa_ndctl.c
else
SOURCE +=\
	region_namespace_none.c\
	numa_none.c
endif

include $(ARCH)/sources.inc

include ../core/pmemcore.inc

SOURCE += $(LIBPMEM2_ARCH_SOURCE)

include ../Makefile.inc

include $(PMEM2)/$(ARCH)/flags.inc

CFLAGS += -I. $(LIBNDCTL_CFLAGS)
LIBS += -pthread $(LIBNDCTL_LIBS)
