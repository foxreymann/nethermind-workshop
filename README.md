# docs

PSUH1 0
PUSH1 0x00

MSTORE (it stores 32 bytes)
MSTORE8 (bad naming - it stoes 8 bits === 1 byte)


# cause StackUnderflowException

POP STOP
ADD STOP

# cause BadInstructionException

INVALID
0xfe

Invalid has been developed if someone wants to throw an exception

# Analyze opcodes JUMP, JUMPI, JUMPDEST and write bytecode that will:
# cause StackOverflowException

jumpdest push1 3 push1 0 jump stop

# Analyze MSTORE, MLOAD operations and write bytecode that will:

 * store 32 bytes in memory at position 0
 * store 2 bytes in memory at position 0
 * store 32 bytes in memory at position 1
 * store 32 bytes in memory at position 32
 * store 0x2a in memory at position 31
 * store 0x2a in memory at position 0

PUSH1 0x2a PUSH1 0 MSTORE8 STOP

# Analyze RETURN opcodes and write bytecode that will:
# return 42

0x60 42 0x60 0 0x52 0x60 1 0x60 31 0xf3
PUSH1 42 PUSH1 0 MSTORE PUSH1 1 MLOAD RETURN
PUSH1 42 PUSH1 0 MSTORE PUSH1 0 PUSH1 1 RETURN STOP

# return 42

0x60 42 0x60 0 0x52 0x60 1 0x60 31 0xf3

# EXTCOPY

PUSH20

# store 1 ehter at address

0x60 10 0x60 18 0x0a 0x73 0x123456789A123456789A 0x55 0x00

# 2 contracts - 1st addition takes 2 arguments, 2nd one calls first one with 2 arguments

CALLDATALOAD offset 0
CALLDATALOAD offset 32
