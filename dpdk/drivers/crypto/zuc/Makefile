# SPDX-License-Identifier: BSD-3-Clause
# Copyright(c) 2016 Intel Corporation

include $(RTE_SDK)/mk/rte.vars.mk

ifneq ($(MAKECMDGOALS),clean)
ifeq ($(LIBSSO_ZUC_PATH),)
$(error "Please define LIBSSO_ZUC_PATH environment variable")
endif
endif

# library name
LIB = librte_pmd_zuc.a

# build flags
CFLAGS += -O3
CFLAGS += $(WERROR_FLAGS)
CFLAGS += -DALLOW_EXPERIMENTAL_API

# versioning export map
EXPORT_MAP := rte_pmd_zuc_version.map

# external library dependencies
CFLAGS += -I$(LIBSSO_ZUC_PATH)
CFLAGS += -I$(LIBSSO_ZUC_PATH)/include
CFLAGS += -I$(LIBSSO_ZUC_PATH)/build
LDLIBS += -L$(LIBSSO_ZUC_PATH)/build -lsso_zuc
LDLIBS += -lrte_eal -lrte_mbuf -lrte_mempool -lrte_ring
LDLIBS += -lrte_cryptodev
LDLIBS += -lrte_bus_vdev

# library source files
SRCS-$(CONFIG_RTE_LIBRTE_PMD_ZUC) += rte_zuc_pmd.c
SRCS-$(CONFIG_RTE_LIBRTE_PMD_ZUC) += rte_zuc_pmd_ops.c

include $(RTE_SDK)/mk/rte.lib.mk
