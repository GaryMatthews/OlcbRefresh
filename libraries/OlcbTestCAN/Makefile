
TOPDIR := $(PWD)
OBJDIR := $(TOPDIR)/obj
CPPFLAGS := -I$(PWD)/../OlcbCommonCAN -I$(PWD)/scaffold $(CPPFLAGS) -I$(PWD)/../OlcbArduinoCAN -DRAMEND=0x0200

SUBDIRS = scaffold ../OlcbCommonCAN test

include standard.mk

.PHONY: all bin lib compile clean

# default target: clean & rebuild
all: clean compile lib bin
	make -C gtest
 
# ToDo:  Automatically create "run" and "reset" command lists
# ToDo:  Move trailing / into OBJDIR, so null name works
# ToDo:  Handle dependency on header files, so "clean" not needed every time

# run all tests
run: all
	$(OBJDIR)/test/CanMrrlcbTest | diff -w - test/results/CanMrrlcbTest.out.txt || echo CanMrrlcbTest failed 1>&2
	$(OBJDIR)/test/StreamTest | diff -w - test/results/StreamTest.out.txt || echo StreamTest failed  1>&2
	$(OBJDIR)/test/DatagramTest | diff -w - test/results/DatagramTest.out.txt || echo DatagramTest failed 1>&2
	$(OBJDIR)/test/NodeMemoryTest | diff -w - test/results/NodeMemoryTest.out.txt || echo NodeMemoryTest failed 1>&2
	$(OBJDIR)/test/ConfigurationTest | diff -w - test/results/ConfigurationTest.out.txt || echo ConfigurationTest failed 1>&2
	$(OBJDIR)/test/PrngTest | diff -w - test/results/PrngTest.out.txt || echo PrngTest failed 1>&2
	gtest/OpenLcbCanBuffer_unittest
	gtest/ButtonProtocol_unittest

# reset the comparison files. Use only if sure new results correct! Commented out to avoid mistakes
reset: 
#	@$(OBJDIR)/test/CanMrrlcbTest > test/results/CanMrrlcbTest.out.txt
#	@$(OBJDIR)/test/StreamTest > test/results/StreamTest.out.txt
#	@$(OBJDIR)/test/DatagramTest > test/results/DatagramTest.out.txt
#	@$(OBJDIR)/test/NodeMemoryTest > test/results/NodeMemoryTest.out.txt
#	@$(OBJDIR)/test/ConfigurationTest > test/results/ConfigurationTest.out.txt
#	@$(OBJDIR)/test/PrngTest > test/results/PrngTest.out.txt
