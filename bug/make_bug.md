make 时出现以下bug
bug : automake 1.13 missing
解决办法:
1. aclocal
2. autoconf
3. automake
4. ./configure   报错 missing something
5. automake --add-missing
6. make
报错libtool版本不对, 将REVISION 后面参数修改为1.3337，macro_revision 1.3337
m4_define([LT_PACKAGE_VERSION], [2.4.6])
m4_define([LT_PACKAGE_REVISION], [1.3337])

AC_DEFUN([LTVERSION_VERSION],
[macro_version='2.4.6'
macro_revision='1.3337'
_LT_DECL(, macro_version, 0, [Which release of libtool.m4 was used?])
_LT_DECL(, macro_revision, 0)
])


