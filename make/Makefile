TARGETS := alpha beta 

#psuedo-target and will not be executed as part as default for make
.nondefault:
	@echo "Execute non-default target"

ifeq (${XC_ARCH}, )
  XC_ARCH:=$(shell go env GOARCH)
endif
export XC_ARCH

ifeq (${ARCHF}, )
  ARCHF:=${XC_ARCH}
  export ARCHF
endif

ifeq (${ARCHC}, )
  ARCHC:=${XC_ARCH}
  export ARCHC
endif

#beta will be executed first, even though alpha is before
$(TARGETS):
	echo ${XC_ARCH}
	echo ${ARCHF}
	echo ${ARCHC}
	@echo $@

#Though recipe is defined above, additional dependency is added
alpha: .nondefault

#Overrides the order to execute beta as default
.DEFAULT_GOAL := beta

#Targets are just actions to be performed and are not associated with files
#Improves performance of make, since there is no need to check if the target requires a rebuild
.PHONY: $(TARGETS)
