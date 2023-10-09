;Introdução ao Assembly
;Autor: Gabriel Bianco Sanches, Feap

SYS_EXIT      equ 1
SYS_READ      equ 3
SYS_WRITE     equ 4
STDIN         equ 0
STDOUT        equ 1

section .data ; Seção de dados
    msg db 'Hello World'
    len equ $ -msg

section .text ; Iniciar seção de texto/mensagem e realocação de memoria
    global _start ; Coleção de dados declarados
    
_start:
    mov edx, len ; comprimento da mensagem 
    mov ecx, msg ; mensagem para escrever
    mov ebx, STDOUT    ; descritor de arquivo(saida)  
    mov eax, SYS_WRITE ; descritor do arquivo(entrada)  
    int 0x80 ; chamada kernel
    mov eax, 1
    int 0x80 ; chamada kernel
