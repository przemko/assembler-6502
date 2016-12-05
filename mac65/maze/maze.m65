RANDOM   =   $D20A
ADDR1    =   $F0
ADDR2    =   $F2
;
         *=  $7000
LOOP     JSR SCROLL
         JSR FILL
         JMP LOOP
;
FILL     LDX #$00
         LDY #$28
LAB1     LDA RANDOM
         AND #$01
         CLC
         ADC #$46
         STA $9FD8,X
         INX
         DEY
         BNE LAB1
         RTS
;
SCROLL   LDA # <$9C40
         STA ADDR1
         LDA # >$9C40
         STA ADDR1+1
         LDA # <$9C68
         STA ADDR2
         LDA # >$9C68
         STA ADDR2+1
         LDX #23
LAB2     LDY #40
LAB3     DEY
         BMI LAB4
         LDA (ADDR2),Y
         STA (ADDR1),Y
         JMP LAB3
LAB4     LDA ADDR2+1
         STA ADDR1+1
         LDA ADDR2
         STA ADDR1
         CLC
         ADC #40
         STA ADDR2
         LDA ADDR2+1
         ADC #$00
         STA ADDR2+1
         DEX
         BNE LAB2 
         RTS
