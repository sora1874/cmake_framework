# The command to remove a file.
RM = cmake -E remove_directory

#cmake definition config
cmake_definition+= -DTOOLCHAIN_PREFIX=riscv64-unknown-elf-
cmake_definition+= -DCHIP=bl702
cmake_definition+= -DBOARD=bl706_iot
cmake_definition+= -DCONFIG_DEBUG=y

build:Makefile
	cmake -S . -B build -G "Unix Makefiles" $(cmake_definition)
	cd build && make -j4

clean:
	$(RM) build

menuconfig:
	python ../../tools/kconfig/menuconfig.py

.PHONY:build clean menuconfig

