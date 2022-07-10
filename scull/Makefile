DEBUG = y

ifeq ($(DEBUG),y)
	DEBFLAGS = -O -g -DSCULL_DEBUG
else
	DEBFLAGS = -O2
endif

ccflags-y += $(DEBFLAGS)

ifneq ($(KERNELRELEASE),)
	scull-objs := main.o
	obj-m := scull.o
else
	KERNELDIR ?= /lib/modules/$(shell uname -r)/build
	PWD := $(shell pwd)

modules:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) modules
endif

clean:
	rm -rf .*.cmd *.symvers *.mod.c *.o *.ko *.mod *.order
