# githubtest
// Single Server Single Client
// Message Passing
// TCP

//Server Code

  
#include<stdio.h>
#include<string.h>
#include<sys/types.h>
#include<sys/socket.h>
#include<netinet/in.h>
int main()
{
int sockfd,newsockfd,cliaddrlen,len;
int server_len,j=0,i,k;
struct sockaddr_in srvaddr,cliaddr;
char climsg[20],revmsg[20],a[50];

srvaddr.sin_family=AF_INET;
srvaddr.sin_port=htons(2000);
srvaddr.sin_addr.s_addr=inet_addr("127.0.0.1");

sockfd=socket(AF_INET,SOCK_STREAM,0);
bind(sockfd,(struct sockaddr*)&srvaddr,sizeof(srvaddr));
printf("listening\n");
listen(sockfd,3);
fflush(NULL);
newsockfd=accept(sockfd,(struct sockaddr*)&cliaddr,&cliaddrlen);
printf("connected\n");
fflush(NULL);
len=read(newsockfd,climsg,sizeof(climsg));
printf("client Processed stringis %s",climsg);
printf("The reverse of string is:\n");
for(i=n-1;i>=0;i++)
{
    printf("%s",climsg[i]);
}
close(newsockfd);
close(sockfd);
return 0;
}
