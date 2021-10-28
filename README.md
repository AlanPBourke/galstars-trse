# galstars-trse


This is a conversion of Jason Aldred's Galencia starfield, taken from his
game of the same name. Jason extracted the starfield ASM code into a standalone
programme (see link below), and this is an Turbo Rascal recreation of that.


 ---------------------------------------------------------------------------------------------------------------------------------
 How It Works 
 ---------------------------------------------------------------------------------------------------------------------------------
 CreateStarScreen fills the entire character screen with the characters and colours defined in StarfieldRow\StarfieldColours.
 The character screen starts at location $0400 and is 25 rows of 40 characters. The screen is filled in such a way that chars
 that are in sequence in the character set will be placed in vertical rows down the screen. 
 Once this procedure is finished the first 4 rows of the screen will have these characters:

```
 :.I..>.QB.V;OWPGLCR.DNC<K?TAS.DXJ=ZBUEAM
 ;.JA.?.RC.W<PXQHMD:.EOD=L.UBTAEYK>.CVFBN
 <.KB...:D.X=QYRINE;AFPE>MAVCUBFZL?.DWGCO
 =.LC.A.;EAY>RZ:JOF<BGQF?NBWDVCG.M..EXHDP
```

 Note the ':' and the ';' below it at the top left. These two characters are numbers 58 and 59 in the character set. We have copied
 the character set into RAM starting at location $3000 (12288 decimal) . 'Star1Ptr' starts off pointing at 'Star1Init', which is 
 location $31D0 (12572 decimal). 12288 - 12572 = 464 bytes or 58 characters. Therefore 'Star1Ptr' starts off pointing at the first
 byte\row of the ':' character in memory. From there the 'DoStarField()' loop will place a star shape into that memory location and 
 on the next pass erase it and draw it one byte down. This produces the falling stars.

 ---------------------------------------------------------------------------------------------------------------------------------
 Resources
 ---------------------------------------------------------------------------------------------------------------------------------
 https://retrocomputing.stackexchange.com/questions/12678/get-exact-position-of-raster-beam-on-c64-c128
 

 https://retrocomputing.stackexchange.com/questions/7528/commodore-8-bit-character-sets/8278
 
 Jason Aldred's original Galencia starfield extracted to a standalone program.
 https://github.com/Jimmy2x2x/C64-Starfield/blob/master/starfield.asm

 Info about the C64 character set.
 https://github.com/neilsf/XC-BASIC/tree/master/examples/invaders
 https://www.c64-wiki.com/wiki/Character_set

 Info about the C64 memory map.
 https://www.pagetable.com/c64ref/c64mem/
 https://github.com/Project-64/reloaded/blob/master/c64/mapc64/MAPC6412.TXT

 GRay Defender's breakdown of how the original ASM works - WATCH THIS.
 https://www.youtube.com/watch?v=47LakVkR5lg&t=1251s
