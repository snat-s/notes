# Código Base
```asmatmel
;******************************************************
; Título del proyecto
;
; Fecha: Poner aquí la fecha
; Autor: Poner aquí el autor
;******************************************************

.include "m16adef.inc"     
   
;******************************************************
;Registros (aquí pueden definirse)
;.def temporal=r19

;Palabras claves (aquí pueden definirse)
;.equ LCD_DAT=DDRC
;******************************************************

.org 0x0000
;Comienza el vector de interrupciones.
jmp RESET ; Reset Handler
jmp EXT_INT0 ; IRQ0 Handler
jmp EXT_INT1 ; IRQ1 Handler
jmp TIM2_COMP ; Timer2 Compare Handler
jmp TIM2_OVF ; Timer2 Overflow Handler
jmp TIM1_CAPT ; Timer1 Capture Handler
jmp TIM1_COMPA ; Timer1 CompareA Handler
jmp TIM1_COMPB ; Timer1 CompareB Handler
jmp TIM1_OVF ; Timer1 Overflow Handler
jmp TIM0_OVF ; Timer0 Overflow Handler
jmp SPI_STC ; SPI Transfer Complete Handler
jmp USART_RXC ; USART RX Complete Handler
jmp USART_UDRE ; UDR Empty Handler
jmp USART_TXC ; USART TX Complete Handler
jmp ADC_COMP ; ADC Conversion Complete Handler
jmp EE_RDY ; EEPROM Ready Handler
jmp ANA_COMP ; Analog Comparator Handler
jmp TWSI ; Two-wire Serial Interface Handler
jmp EXT_INT2 ; IRQ2 Handler
jmp TIM0_COMP ; Timer0 Compare Handler
jmp SPM_RDY ; Store Program Memory Ready Handler
; Termina el vector de interrupciones.

;******************************************************
;Aquí comenzará el programa
;******************************************************
Reset:
;Primero inicializamos el stack pointer...
ldi r16, high(RAMEND)
out SPH, r16
ldi r16, low(RAMEND)
out SPL, r16 


;******************************************************
;No olvides configurar al inicio los puertos que utilizarás
;También debes configurar si habrá o no pull ups en las entradas
;Para las salidas deberás indicar cuál es la salida inicial
;Los registros que vayas a utilizar inicializalos si es necesario
;******************************************************






;******************************************************
;Aquí están las rutinas para el manejo de las interrupciones concretas
;******************************************************
EXT_INT0: ; IRQ0 Handler
reti
EXT_INT1: 
reti ; IRQ1 Handler
TIM2_COMP: 
reti ; Timer2 Compare Handler
TIM2_OVF: 
reti ; Timer2 Overflow Handler
TIM1_CAPT: 
reti ; Timer1 Capture Handler
TIM1_COMPA: 
reti ; Timer1 CompareA Handler
TIM1_COMPB: 
reti ; Timer1 CompareB Handler
TIM1_OVF: 
reti ; Timer1 Overflow Handler
TIM0_OVF: 
reti ; Timer0 Overflow Handler
SPI_STC: 
reti ; SPI Transfer Complete Handler
USART_RXC: 
reti ; USART RX Complete Handler
USART_UDRE: 
reti ; UDR Empty Handler
USART_TXC: 
reti ; USART TX Complete Handler
ADC_COMP: 
reti ; ADC Conversion Complete Handler
EE_RDY: 
reti ; EEPROM Ready Handler
ANA_COMP: 
reti ; Analog Comparator Handler
TWSI: 
reti ; Two-wire Serial Interface Handler
EXT_INT2: 
reti ; IRQ2 Handler
TIM0_COMP: 
reti
SPM_RDY: 
reti ; Store Program Memory Ready Handler
```
# Prácticas
## Práctica 1
- Utilizar el micro controlador como un cable.

### Aprendido

- Aprender a recibir una carga y sacarla.

``` asmatmel
; el main se tiene que utilizar
;; Configuración de entradas y salidas
ldi r16, 0b0000_0000 ; 0x00, 0
out ddra, r16 ;; puerto A como entrada

ldi r16, 0b1111_1111 ; 0xFF, 255
out portA, r16 ;; Port A tiene pull ups

ldi r16, 0b1111_1111 ; 0xFF, 255
out ddrc, r16 ;; Puerto c es la salida

ldi r16, 0b0000_0000
out portC, r16 ;; Puerto C empieza apagado.

;; fin de la configuración

main:
in r16, pinA ;; leer puerto completo (los 8 bits)
com r16 ;; complemento a uno
out portC, r16 ;; Sacamos por el otro puerto la información
rjmp main
```


## Práctica 2
- Utilizar un micro para convertir de un dipswitch a un display de siete segmentos.

### Aprendido
- Utilizar if, que en este caso son dos instrucciones, `cpi` (compare) y `breq` (branch if equal).
- También aprendí un poco a leer el manual que en este caso tenía una instrucción muy útil llamada `brge` (branch if grater or equal).

``` asmatmel
main:
	in r16, PINA ;; leer puerto completo (los 8 bits)
	com r16
	cpi r16, 10
	brge MAYOR 

	cpi  r16, 0 ;; Comparo entre un registro y un número
	breq CERO
	
	cpi  r16, 1 ;; Comparo entre un registro y un número
	breq UNO
	
	cpi  r16, 2 ;; Comparo entre un registro y un número
	breq DOS
	
	cpi  r16, 3 ;; Comparo entre un registro y un número
	breq TRES
	
	cpi  r16, 4 ;; Comparo entre un registro y un número
	breq CUATRO
	
	cpi  r16, 5 ;; Comparo entre un registro y un número
	breq CINCO
	
	cpi  r16, 6 ;; Comparo entre un registro y un número
	breq SEIS
	
	cpi  r16, 7 ;; Comparo entre un registro y un número
	breq SIETE
	
	cpi  r16, 8 ;; Comparo entre un registro y un número
	breq OCHO
	
	cpi  r16, 9 ;; Comparo entre un registro y un número
	breq NUEVE
	
rjmp main

	CERO:
		ldi r16, 0b0_100_0000 ;; Ánodo común
		out PORTC, r16
		rjmp main
	UNO:
		ldi r16, 0b0_111_1001
		out PORTC, r16
		rjmp main
	DOS:
		ldi r16, 0b0_010_0100
		out PORTC, r16
		rjmp main
	TRES:
		ldi r16, 0b0_011_0000
		out PORTC, r16
		rjmp main
	CUATRO:
		ldi r16, 0b0_001_1001
		out PORTC, r16
		rjmp main
	CINCO:
		ldi r16, 0b0_001_0010
		out PORTC, r16
		rjmp main
	SEIS:
		ldi r16, 0b0_000_0010
		out PORTC, r16
		rjmp main
	SIETE:
		ldi r16, 0b0_111_1000
		out PORTC, r16
		rjmp main
	OCHO:
		ldi r16, 0b0_000_0000
		out PORTC, r16
		rjmp main
	NUEVE:
		ldi r16, 0b001_1000
		out PORTC, r16
		rjmp main

	MAYOR:
		ldi r16, 0b111_1111
		out PORTC, r16
		rjmp main
```

## Práctica 3
- Contador con un botón.

### Aprendido
- El rebote de un botón te da ruido, entonces aprendimos a quitar el ruido que te da un botón. 
- Leer de un solo pin con la instrucción `sbis` .
``` asmatmel
;; configuración de puertos
main:
sbis PINA, 0
rjmp boton
out PORTD, r16
rjmp main

boton:
;; Código al apretar
rcall RETARDO
traba_0:
	sbis pina, 0
	rjmp traba_0
rcall RETARDO
;; Código al soltar
inc r16
cpi r16, 10
brge resetear

rjmp main

resetear:
	ldi r16, 0
	rjmp main

RETARDO:
; ============================= 
;    delay loop generator 
;     50000 cycles:
; ----------------------------- 
; delaying 49995 cycles:
          ldi  R17, $65
WGLOOP0:  ldi  R18, $A4
WGLOOP1:  dec  R18
          brne WGLOOP1
          dec  R17
          brne WGLOOP0
; ----------------------------- 
; delaying 3 cycles:
          ldi  R17, $01
WGLOOP2:  dec  R17
          brne WGLOOP2
; ----------------------------- 
; delaying 2 cycles:
          nop
          nop
; ============================= 
```
## Práctica 4

- Contadores independientes.

Los contadores son independientes y además tienen que tener un reset.

Son ocho leds, cuatro separados.
### Aprendido
``` asm
```

## Práctica 5 (Teclado Matricial)
#### Teclados Matriciales
- Son completamente escalables.
- Se basan en filas y columnas.
- No se le tienen que poner resistencias.
```asmatmel
ldi ddra, 0b0000_1111
ldi portA, 0b1111_1111
```
### Teclado para Proteus

La idea para los teclados es sencilla: 
- Tienes un mega switch 
- Tienes funciónes en cada uno de las comparaciónes que hacen lo que quieres.

```asmatmel
;******************************************************
; Teclado matricial
;
; Fecha: 2022-10-04
; Autor: Santiago Pedroza Díaz
;******************************************************

.include "m16adef.inc"     
   
;******************************************************
;Registros (aquí pueden definirse)
;.def temporal=r19
.def izquierda=r17
.def derecha=r18
.def salida=r19
;Palabras claves (aquí pueden definirse)
;.equ LCD_DAT=DDRC
;******************************************************

.org 0x0000
;Comienza el vector de interrupciones.
jmp RESET ; Reset Handler
jmp EXT_INT0 ; IRQ0 Handler
jmp EXT_INT1 ; IRQ1 Handler
jmp TIM2_COMP ; Timer2 Compare Handler
jmp TIM2_OVF ; Timer2 Overflow Handler
jmp TIM1_CAPT ; Timer1 Capture Handler
jmp TIM1_COMPA ; Timer1 CompareA Handler
jmp TIM1_COMPB ; Timer1 CompareB Handler
jmp TIM1_OVF ; Timer1 Overflow Handler
jmp TIM0_OVF ; Timer0 Overflow Handler
jmp SPI_STC ; SPI Transfer Complete Handler
jmp USART_RXC ; USART RX Complete Handler
jmp USART_UDRE ; UDR Empty Handler
jmp USART_TXC ; USART TX Complete Handler
jmp ADC_COMP ; ADC Conversion Complete Handler
jmp EE_RDY ; EEPROM Ready Handler
jmp ANA_COMP ; Analog Comparator Handler
jmp TWSI ; Two-wire Serial Interface Handler
jmp EXT_INT2 ; IRQ2 Handler
jmp TIM0_COMP ; Timer0 Compare Handler
jmp SPM_RDY ; Store Program Memory Ready Handler
; Termina el vector de interrupciones.

;******************************************************
;Aquí comenzará el programa
;******************************************************
Reset:
;Primero inicializamos el stack pointer...
ldi r16, high(RAMEND)
out SPH, r16
ldi r16, low(RAMEND)
out SPL, r16 


;******************************************************
;No olvides configurar al inicio los puertos que utilizarás
;También debes configurar si habrá o no pull ups en las entradas
;Para las salidas deberás indicar cuál es la salida inicial
;Los registros que vayas a utilizar inicializalos si es necesario
;******************************************************

ldi r16, 0b0000_1111
out DDRA, r16
ldi r16, 0b1111_1111
out DDRD, r16
ldi r16, 0
out PORTD, r16

;; Iniciación global
ldi r17, 0
ldi r18, 0

main:
    nop
	nop
	nop
	nop
	ldi r16, 0b1111_1111
	out PORTA, r16
	nop
	nop
	;;ldi r16, 0b1111_0111 ;; para el físico
	ldi  r16, 0b1111_1110
	out PORTA, r16
	nop
	nop
	sbis PINA, 6
	rjmp cero
	
	;; Comparaciones para la fila del cero
	;;sbis PINA, 5
	;;rjmp CERO

	;; Comparaciones para la fila del 7, 8, 9
	ldi r16, 0b1111_0111 ;; para el físico
	out PORTA, r16
	nop
	nop
	sbis PINA, 7
	rjmp siete
	sbis PINA, 6
	rjmp ocho
	sbis PINA, 5
	rjmp nueve

	;; Comparaciones para 4, 5, 6
	ldi r16, 0b1111_1011 ;; para el físico
	out PORTA, r16
	nop
	nop
	sbis PINA, 7
	rjmp cuatro
	sbis PINA, 6
	rjmp cinco
	sbis PINA, 5
	rjmp seis

	;; Comparaciones para 1, 2, 3
	ldi r16, 0b1111_1101 ;; para el físico
	out PORTA, r16
	nop
	nop
	sbis PINA, 7
	rjmp uno
	sbis PINA, 6
	rjmp dos
	sbis PINA, 5
	rjmp tres

rjmp main

CERO:
	rcall RETARDO
	traba_0:
		sbis PINA, 6
		rjmp traba_0
	rcall RETARDO
rjmp main
UNO:
	rcall RETARDO
	traba_1:
		sbis PINA, 7
		rjmp traba_1
	rcall RETARDO
rjmp main

DOS:
	rcall RETARDO
	traba_2:
		sbis PINA, 6
		rjmp traba_2
	rcall RETARDO
rjmp main

TRES:
	rcall RETARDO
	traba_3:
		sbis PINA, 5
		rjmp traba_3
	rcall RETARDO
rjmp main
CUATRO:
	rcall RETARDO
	traba_4:
		sbis PINA, 7
		rjmp traba_4
	rcall RETARDO
rjmp main

CINCO:
	rcall RETARDO
	traba_5:
		sbis PINA, 6
		rjmp traba_5
	rcall RETARDO
rjmp main

SEIS:
	rcall RETARDO
	traba_6:
		sbis PINA, 5
		rjmp traba_6
	rcall RETARDO
rjmp main

SIETE:
	rcall RETARDO
	traba_7:
		sbis PINA, 7
		rjmp traba_7
	rcall RETARDO
rjmp main

OCHO:
	rcall RETARDO
	traba_8:
		sbis PINA, 6
		rjmp traba_8
	rcall RETARDO
rjmp main

NUEVE:
	rcall RETARDO
	traba_9:
		sbis PINA, 5
		rjmp traba_9
	rcall RETARDO
rjmp main


RETARDO:
; ============================= 
;    delay loop generator 
;     50000 cycles:
; ----------------------------- 
; delaying 49995 cycles:
          ldi  R22, $65
WGLOOP0:  ldi  R23, $A4
WGLOOP1:  dec  R23
          brne WGLOOP1
          dec  R22
          brne WGLOOP0
; ----------------------------- 
; delaying 3 cycles:
          ldi  R22, $01
WGLOOP2:  dec  R22
          brne WGLOOP2
; ----------------------------- 
; delaying 2 cycles:
          nop
          nop
; ============================= 



;******************************************************
;Aquí están las rutinas para el manejo de las interrupciones concretas
;******************************************************
EXT_INT0: ; IRQ0 Handler
reti
EXT_INT1: 
reti ; IRQ1 Handler
TIM2_COMP: 
reti ; Timer2 Compare Handler
TIM2_OVF: 
reti ; Timer2 Overflow Handler
TIM1_CAPT: 
reti ; Timer1 Capture Handler
TIM1_COMPA: 
reti ; Timer1 CompareA Handler
TIM1_COMPB: 
reti ; Timer1 CompareB Handler
TIM1_OVF: 
reti ; Timer1 Overflow Handler
TIM0_OVF: 
reti ; Timer0 Overflow Handler
SPI_STC: 
reti ; SPI Transfer Complete Handler
USART_RXC: 
reti ; USART RX Complete Handler
USART_UDRE: 
reti ; UDR Empty Handler
USART_TXC: 
reti ; USART TX Complete Handler
ADC_COMP: 
reti ; ADC Conversion Complete Handler
EE_RDY: 
reti ; EEPROM Ready Handler
ANA_COMP: 
reti ; Analog Comparator Handler
TWSI: 
reti ; Two-wire Serial Interface Handler
EXT_INT2: 
reti ; IRQ2 Handler
TIM0_COMP: 
reti
SPM_RDY: 
reti ; Store Program Memory Ready Handler
```
## Práctica 6

- Motores a pasos.

Podemos anclar un motor todas las bobinas en un motor y puede que falle un circuito.
### Pseudocódigo
```
ldi rx, 0b0000_0001 ;; <- DCBA el nibble menos significativo.
RETARDO
out PORTx, Rx
ldi Rx, 0b0000_0010
out PORTx, Rx
ldi Rx, 0b0000_0100
```
### Motores de paso unipolares
El marrón es la tierra.
- Cuatro cables y la tierra.
### Aprendido
``` asm
```

## Práctica 8
```asmatmel
sei ;; es para activar automáticamente el business de las interrupciones.
```
Para interrupciónes externas se usa el registro *MCUCR*. 
**MCUCR:** Determina la manera de activamiento de las interrupciónes 0 y 1.

Antes de declarar los puertos se pone esto. 
```asmatmel
ldi r16, 0b0000_00_11
out MCUCR, r16
```

Dos ceros hacen que no uses una interrupción en específico.

También tenemos el MCUCSR que solo funciona para la interrupción 2.

El bit 6 es el que se modifica como tal.

```asmatmel

```

### GICR
Se habilitan las interrupciones.
|Bit 7| Bit 6 |Bit 5 | Bit 4 | Bit 3 | Bit 2 | Bit  1| Bit 0 |
|-----|-------|------|-------|-------|-------|-------|-------|
| INT1| INT0 | INT2 | - | - | - | IVSEL | IVCE|

### GIFR
Son las banderas de interrupción que se generan para saber si existe. *Primero va el **GIFR** y después el **GICR**.* 
- **Todas se setean en 1**.
|Bit 7| Bit 6 |Bit 5 | Bit 4 | Bit 3 | Bit 2 | Bit  1| Bit 0 |
|-----|-------|------|-------|-------|-------|-------|-------|
|INTF1|INTF0  |INTF2 | -     | -     | -     | -     |-      |

## Aprendido
```asmatmel
sei ;; instrucción que inicializa las interrupciones externas.
ldi r16, 0b0000_00_11
out MCUCR, r16
ldi r16, 0b111_0_0000
out GIFR, r16
ldi r16, 0b010_000_00
out GICR, r16
```

