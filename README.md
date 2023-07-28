# atmel Platformio 유용한 정보
AVR CPU 관련

## USB driver installation made easy
[zadig]https://zadig.akeo.ie/  

## AVR® Fuse Calculator
[fuse]https://www.engbedded.com/fusecalc/  

## Development Platforms Atmel AVR Platforio
[platforio]https://docs.platformio.org/en/stable/platforms/atmelavr.html  

# Platformio Platform option

tool : avrisp mkii  
chip : atmega328p  
xtal : 16MHz  

### platform : 
```
atmelavr
```

### board
```
uno
```

### framework
```
arduino
```

### upload_port
```
usb
```

### upload_protocol
```
custom
```

### upload_flags
```
-C
${platformio.packages_dir}/tool-avrdude/avrdude.conf
-p
$BOARD_MCU
-P
$UPLOAD_PORT
-c
stk500v2
```

### upload_command
* flash upload  
```
avrdude $UPLOAD_FLAGS -U flash:w:$SOURCE:i  
```

* if you need chip fuse 1MHz (RC original f/8)  & flash upload  
```
avrdude $UPLOAD_FLAGS -U lfuse:w:0x62:m -U hfuse:w:0xd9:m -U efuse:w:0xff:m -U flash:w:$SOURCE:i  
```

* if you need chip fuse 8MHz & BOD 2.7v (RC f/1)  & flash upload  
```
avrdude $UPLOAD_FLAGS -U lfuse:w:0xe2:m -U hfuse:w:0xd9:m -U efuse:w:0xfd:m -U flash:w:$SOURCE:i  
```

* if you need chip fuse 16MHz ext & BOD 2.7v (ext xtal)  & flash upload  
```
avrdude $UPLOAD_FLAGS -U lfuse:w:0xef:m -U hfuse:w:0xd9:m -U efuse:w:0xfd:m -U flash:w:$SOURCE:i  
```

## flash program 에러 발생시
zadig 실행하여 32bit 드라이버로 downgrade  
<img src="[/path/to/img.jpg](https://github.com/copaland/atmel/blob/main/image/zadig.png?raw=true)" width="450px" height="300px" title="px(픽셀) 크기 설정" alt="zadig"></img><br/>
