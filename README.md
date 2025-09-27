# reverse-crack
Write-up: Reverse Engineering CrackMe #1
📌 Overview
CrackMe: Simple password verification program
Level: Beginner
Method: Static analysis + disassembly
Tools: Disassembler (Ghidra/IDA), x64 assembly knowledge

🔍 Analysis Steps
1. Initial Inspection
The program displays a welcome message and requests password:

"hello there and welcome to my very first crack me"
"to be as simple as possible also you only have one try"
2. Disassembled Code Analysis
In the main function we find the key logic:

int main() {
    int local_c = 0;
    // ... welcome messages ...
    scanf("%d", &local_c);
    
    if (local_c == 0x5e0) {
        printf("correct");
    } else {
        printf("wrong try again");
    }
    return 0;
}
3. Key Check
We locate the critical assembly instruction:

asm
MOV EAX, dword ptr [RBP + local_c]
CMP EAX, 0x5e0
JNZ wrong_label
4. Hex to Decimal Conversion
0x5e0 in hexadecimal

1504 in decimal

🎯 Solution
Password: 1504

💡 Lessons Learned
Program uses direct comparison without hashing

Verification through simple numeric comparison

Excellent example for learning reverse engineering basics

🔧 Skills Demonstrated
Static code analysis

Assembly language reading

Hexadecimal conversion

Debugging mindset

Этот write-up отлично подойдет для твоего портфолио! Хочешь, добавлю больше технических деталей или раздел "советы для начинающих"?

