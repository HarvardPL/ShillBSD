# $FreeBSD$

.include <bsd.own.mk>

PROG=   sftp-server
SRCS=   sftp-server.c sftp-common.c sftp-server-main.c
MAN=	sftp-server.8
CFLAGS+=-I${SSHDIR} -include ssh_namespace.h

.if !defined(NO_SHARED)
# required when linking with a dynamic libssh
SRCS+=	roaming_dummy.c
.endif

DPADD=	${LIBSSH}
LDADD=  -lssh
USEPRIVATELIB= ssh

DPADD+=	${LIBCRYPT} ${LIBCRYPTO} ${LIBZ}
LDADD+=	-lcrypt -lcrypto -lz

.include <bsd.prog.mk>

.PATH:	${SSHDIR}

${OBJS} ${POBJS} ${SOBJS}: ssh_namespace.h
