
# デフォルト動作

default :
	../z_tools/make.exe run

# ファイル生成規則

OS-Ishida.bin : OS-Ishida.nas Makefile
	../z_tools/nask.exe OS-Ishida.nas OS-Ishida.bin OS-Ishida.lst

helloos.img : OS-Ishida.bin Makefile
	../z_tools/edimg.exe   imgin:../z_tools/fdimg0at.tek \
		wbinimg src:OS-Ishida.bin len:512 from:0 to:0   imgout:helloos.img

#コマンド

asm :
	../z_tools/make.exe -r OS-Ishida.bin

img :
	../z_tools/make.exe -r helloos.img

run :
	../z_tools/make.exe img
	copy helloos.img ..\z_tools\qemu\fdimage0.bin
	../z_tools/make.exe -C ../z_tools/qemu

install :
	../z_tools/make.exe img
	../z_tools/imgtol.com w a: helloos.img

lcean :
	-del OS-Ishida.bin
	-del OS-Ishida.lst

src_only :
	../z_tools/make.exe clean
	-del helloos.img