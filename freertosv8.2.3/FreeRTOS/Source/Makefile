BUILDDIR= ../../../build
SRC= $(wildcard *.c)
SRCPORTC= ./portable/GCC/$(TARGET_CPU)/port.c
#SRCASM= ./portable/GCC/$(TARGET_CPU)/cpu_s.S
SRCMEM= ./portable/MemMang/heap_4.c
OBJ= $(SRC:.c=.o)
OBJ+=$(SRCPORTC:port.c=port.o)
#OBJ+=$(SRCASM:cpu_s.S=cpu_s.o)
OBJ+=$(SRCMEM:heap_4.c=heap_4.o)
TAR = freertos.a
INC_DIR	= ../../../include
INC1_DIR = ../../FreeRTOS

CFLAGS += -I$(INC_DIR) \
			-I$(INC_DIR)/$(SOC) \
			-I$(INC_DIR)/csky \
			-I$(INC_DIR)/lib \
			-I$(INC1_DIR)/Source/include \
			-I$(INC1_DIR)/Source/portable/GCC/$(TARGET_CPU)

all: $(TAR)


%.o: %.c
	$(CC) $(CFLAGS) $< -o $@

%.o: %.s
	$(AS) $(AFLAGS) $< -o $@

%.o: %.S
	$(CC) $(CFLAGS) $< -o $@

$(TAR): $(OBJ)
	$(AR) r $(BUILDDIR)/$(TAR) $(OBJ)
#	$(RM) -rf $(OBJ)
	mv $(OBJ) $(BUILDDIR)


clean:
	$(RM) -rf $(BUILDDIR)/*.o
	$(RM) -rf $(BUILDDIR)/*.a
	$(RM) -rf $(BUILDDIR)/*.elf

