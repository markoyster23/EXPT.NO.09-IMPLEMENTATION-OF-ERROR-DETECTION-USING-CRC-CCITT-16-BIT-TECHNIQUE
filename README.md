# EXPT.NO.09-IMPLEMENTATION-OF-ERROR-DETECTION-USING-CRC-CCITT-16-BIT-TECHNIQUE
# AIM:
To write a program for error Detection using Cyclic Redundancy Check (CRC-16 bit) technique.

# EQUIPMENTS REQUIRED:
1.	Personal Computer
   
2.	C++ compiler

# ALGORITHM:
1] Open code blocks application and create a new file.  
2] After creating the file type the codes.  
3] After typing the codes save the file using the .c extension in the desired location. 4] Run the program using build and run.  
5] Give polynomial values and the generated polynomial is obtained, and by other means arraive	at the desired output which uses the error detection technique.  
6] Thus the output polynomial is obtained through this technique.  

# PROGRAM:
```
#include <stdio.h>
#include <string.h>

unsigned short crc_ccitt(unsigned char *data, int length)
{
    unsigned short crc = 0xFFFF;

    for(int i = 0; i < length; i++)
    {
        crc ^= (unsigned short)data[i] << 8;

        for(int j = 0; j < 8; j++)
        {
            if(crc & 0x8000)
                crc = (crc << 1) ^ 0x1021;
            else
                crc = crc << 1;
        }
    }

    return crc;
}

int main()
{
    char data[100];

    printf("Enter data: ");
    scanf("%s", data);

    unsigned short crc = crc_ccitt((unsigned char*)data, strlen(data));

    printf("\nEntered Data : %s", data);
    printf("\nCRC-CCITT    : %04X", crc);

    return 0;
}
```
# OUTPUT:

<img width="1280" height="960" alt="WhatsApp Image 2026-06-05 at 8 12 52 AM" src="https://github.com/user-attachments/assets/68a2ef42-59dd-459f-9b68-acdb4c6e44c8" />


# RESULT:

Thus the error detection using CRC-CCITT[16 bit] technique is implemented and the output is obtained and verified successfully.
