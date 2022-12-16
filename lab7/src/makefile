CGLAGS=-Wall -Wextra

all: tcpclient tcpserver udpclient udpserver

clean: 
	rm -rf *.out

rebuild: clean all

r: rebuild

tcpclient: tcpclient.c
	gcc $(CGLAGS) -D BUFSIZE=2 -D SADDR='struct sockaddr' -D SIZE='sizeof(struct sockaddr_in)' tcpclient.c -o tcp_clent.out
tcpserver: tcpserver.c
	gcc $(CGLAGS) -D SERV_PORT=10050 -D BUFSIZE=100  -D SADDR='struct sockaddr' tcpserver.c -o tcp_serv.out
udpclient: udpclient.c
	gcc $(CGLAGS) -D SERV_PORT=20001 -D BUFSIZE=1024 -D SADDR='struct sockaddr' -D SLEN='sizeof(struct sockaddr_in)' udpclient.c -o udp_client.out
udpserver: udpserver.c
	gcc $(CGLAGS) -D SERV_PORT=20001 -D BUFSIZE=1024 -D SADDR='struct sockaddr' -D SLEN='sizeof(struct sockaddr_in)' udpserver.c -o udp_serv.out

CC=gcc

all: udpservermake udpclimake tcpservermake tcpclitmake

udpservermake: udpserver.c
	$(CC) -o udpserv udpserver.c -D SERV_PORT=20001 -D BUFSIZE=1024 -D SADDR='struct sockaddr' -D SLEN='sizeof(struct sockaddr_in)'

udpclimake: udpclient.c
	$(CC) -o udpcli udpclient.c -D SERV_PORT=20001 -D BUFSIZE=1024 -D SADDR='struct sockaddr' -D SLEN='sizeof(struct sockaddr_in)'

tcpservermake: tcpserver.c
	$(CC) -o tcpserv tcpserver.c -D SERV_PORT=10050 -D BUFSIZE=100  -D SADDR='struct sockaddr'

tcpclitmake: tcpclient.c
	$(CC) -o tcpcli tcpclient.c -D BUFSIZE=100 -D SADDR='struct sockaddr' -D SIZE='sizeof(struct sockaddr_in)'