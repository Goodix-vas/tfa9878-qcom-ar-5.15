ifneq ($(CONFIG_SND_SOC_TFA9878),)
# TFA audio amplifier - TFA9878

ifeq ($(CONFIG_SND_SOC_TFA9878),m)
TFA_KERNEL_MODULE        =1
endif

TFA_VERSION              =tfa9878

TFA98XX_FLAGS            := -DUSE_TFA9878
ifeq ($(CONFIG_PLATFORM_QUALCOMM),y)
TFA98XX_FLAGS            += -DQPLATFORM
endif

# cc flags
#ccflags-y              := -DDEBUG
ccflags-y               += -Werror

# objs
snd-soc-tfa98xx-objs    := tfa98xx.o
snd-soc-tfa98xx-objs    += tfa_container.o
snd-soc-tfa98xx-objs    += tfa_dsp.o
snd-soc-tfa98xx-objs    += tfa_init.o
ifdef TFA_DEBUG
snd-soc-tfa98xx-objs    += tfa_debug.o
endif

# CFLAGS
CFLAGS_tfa98xx.o       += $(TFA98XX_FLAGS)
CFLAGS_tfa_container.o += $(TFA98XX_FLAGS)
CFLAGS_tfa_dsp.o       += $(TFA98XX_FLAGS)
CFLAGS_tfa_init.o      += $(TFA98XX_FLAGS)
ifdef TFA_DEBUG
CFLAGS_tfa_debug.o     += $(TFA98XX_FLAGS)
endif

ifdef TFA_KERNEL_MODULE
# module driver
obj-m   := snd-soc-tfa98xx.o
ifdef TFA_USE_TFA_CLASS
obj-m   += snd-soc-tfa_sysfs.o
endif
else
# built-in driver
obj-y	+= snd-soc-tfa98xx.o
endif

endif
