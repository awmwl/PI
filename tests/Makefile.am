ACLOCAL_AMFLAGS = ${ACLOCAL_FLAGS} -I m4

if WITH_CLI_TESTS
MAYBE_CLI_TESTS = CLI
endif

SUBDIRS = . $(MAYBE_CLI_TESTS)

AM_CPPFLAGS += \
-I$(top_srcdir)/include \
-I$(top_srcdir)/src \
-I$(top_srcdir)/lib \
-I$(top_srcdir)/third_party/unity/include \
-isystem$(top_srcdir)/third_party/cJSON/include \
-isystem$(top_srcdir)/third_party/uthash/src \
-DTESTDATADIR=\"$(abs_srcdir)/testdata\"

TESTS = \
test_bmv2_json_reader \
test_getnetv \
test_p4info \
test_frontends_generic

common_source = main.c utils.c utils.h

test_bmv2_json_reader_SOURCES = $(common_source) test_bmv2_json_reader.c
test_bmv2_json_reader_CPPFLAGS = $(AM_CPPFLAGS) -DTEST_BMV2_JSON_READER

test_getnetv_SOURCES = $(common_source) test_getnetv.c
test_getnetv_CPPFLAGS = $(AM_CPPFLAGS) -DTEST_GETNETV

test_p4info_SOURCES = $(common_source) test_p4info.c
test_p4info_CPPFLAGS = $(AM_CPPFLAGS) -DTEST_P4INFO

test_frontends_generic_SOURCES = $(common_source) frontends/generic/test.c
test_frontends_generic_CPPFLAGS = $(AM_CPPFLAGS) -DTEST_FRONTENDS_GENERIC

test_all_SOURCES = $(common_source) \
test_bmv2_json_reader.c \
test_getnetv.c \
test_p4info.c \
frontends/generic/test.c
test_all_CPPFLAGS = $(AM_CPPFLAGS) \
-DTEST_BMV2_JSON_READER \
-DTEST_GETNETV \
-DTEST_P4INFO \
-DTEST_FRONTENDS_GENERIC

# libpi needs to come before libpi_dummy, because it uses it
LDADD = \
$(top_builddir)/src/libpi.la \
$(top_builddir)/src/libpifegeneric.la \
$(top_builddir)/targets/dummy/libpi_dummy.la \
$(top_builddir)/src/libpip4info.la \
$(top_builddir)/third_party/unity/libunity.la \
$(top_builddir)/third_party/cJSON/libpicjson.la \
$(top_builddir)/lib/libpitoolkit.la

check_PROGRAMS = \
test_bmv2_json_reader \
test_getnetv \
test_p4info \
test_frontends_generic \
test_all

EXTRA_DIST = \
testdata/simple_router.json \
testdata/valid.json \
testdata/ecmp.json \
testdata/stats.json \
testdata/l2_switch.json \
testdata/pragmas.json \
testdata/unittest.p4 \
testdata/unittest.p4info.txt \
testdata/id_collision.json \
testdata/act_prof.json \
testdata/reconcile_1.p4info.txt \
testdata/reconcile_2.p4info.txt \
testdata/reconcile_3.p4info.txt \
testdata/customids.p4 \
testdata/customids.p4info.txt

# cleaning up the file created by the dummy target (function call counters)
clean-local:
	rm -f $(builddir)/func_counter.txt
