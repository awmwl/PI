ACLOCAL_AMFLAGS = ${ACLOCAL_FLAGS} -I m4

# include path for protoc-generated code will change when we agree on an
# installation path
AM_CPPFLAGS = \
-I$(top_srcdir)/../include \
-I$(top_builddir)/cpp_out \
-I$(top_srcdir)/../frontends_extra/cpp

AM_CXXFLAGS = -Wall -Werror

libpifeproto_la_SOURCES = \
src/device_mgr.cpp

nobase_include_HEADERS = \
PI/frontends/proto/device_mgr.h

lib_LTLIBRARIES = libpifeproto.la