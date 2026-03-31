
## Ex-5 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.


STEP-2: Arrange the plain text in row columnar matrix format.

STEP-3: Now read the keyword depending on the number of columns of the plain text.

STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.

STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```
#include <stdio.h>
#include <string.h>

void rail(char *m,int r,char *c,int d){
    int n=strlen(m),i,j,k=0,row=0,dir=1;
    char a[r][n]; memset(a,'\n',sizeof(a));

    for(i=0;i<n;i++){                 // mark / fill
        a[row][i]= d? '*' : m[i];
        if(row==0) dir=1; else if(row==r-1) dir=-1;
        row+=dir;
    }

    if(d)                             // fill cipher into pattern
        for(i=0;i<r;i++)
            for(j=0;j<n;j++)
                if(a[i][j]=='*') a[i][j]=m[k++];

    row=0; dir=1;
    for(i=0;i<n;i++){                 // read zigzag
        c[i]=a[row][i];
        if(row==0) dir=1; else if(row==r-1) dir=-1;
        row+=dir;
    }
    c[n]=0;

    if(!d){                           // encryption output order
        k=0;
        for(i=0;i<r;i++)
            for(j=0;j<n;j++)
                if(a[i][j]!='\n') c[k++]=a[i][j];
        c[k]=0;
    }
}

int main(){
    char m[100],c[100],p[100];
    int r;

    printf("Msg & rails: ");
    fgets(m,100,stdin);
    m[strcspn(m,"\n")]=0;
    scanf("%d",&r);

    rail(m,r,c,0);
    printf("Enc: %s\n",c);

    rail(c,r,p,1);
    printf("Dec: %s\n",p);

    return 0;
}
 
```

# OUTPUT
<img width="405" height="173" alt="image" src="https://github.com/user-attachments/assets/ef2ea458-5a1b-4427-8804-ce03cb3e5706" />


# RESULT

The program is executed successfully
