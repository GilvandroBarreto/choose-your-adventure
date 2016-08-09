.data
vetor: .word 0:9
i:  .word 0
contador: .word 0
numero: .word
soma: .word 0
nomeArq: .asciiz "resultado.txt"
msg1: .asciiz "Informe um número"

.text
.global main 			# main() como ponto de inicio

main:	la $a0, msg1	# endereco da string a ser impressa (printf)
		li $v0, 4		# print string
		syscall

		li $v0, 5		# read integer
		syscall
		move $s0, $v0	# copia valor lido (numero) para $s0
		# laco while - mapeamento de variaveis para registradores #
		la $s1, contador
		li $s2, 10 		# contador para laco while e for
		la $s3, i
		la $s4, vetor
		
		lw $s1, 0($s1) 			# le o valor do contador
		lw $s3, 0($s3)			# le o valor de i

lwhile: bge $s1, $s2, sailaco I
		add $t0, $s1, $s0		# contador + numero
		sll $s3, $s3, 2			# i * 4 - alinhamento de índice
		add $t1, $s4, $s3 		#vetor[i]
		sw $t0, 0($t1)			# vetor[i] = contador + numero
		addi $s3, $s3, 1		# i++
		addi $s1, $s1, 1		# contador++
		j lwhile				#retorna para while

sailaco: 




saída:	li $v0, 10		# serviço de finalização do programa
		syscall 

















#############  mapeamento de registradores #########

		numero = $s0
		contador = $s1
		10 = $s2
		i = $s3
		vetor = $s4
