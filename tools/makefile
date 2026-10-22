# p8js helper drivers, built against the parent z8lua liblua.a.
#
#   make -C .. a MYLIBS=      # build ../liblua.a first (MYLIBS= drops readline)
#   make -C tools             # build the drivers below
#
# p8luac     — luac-style bytecode dumper: stdin/file -> z8lua dump (Lua 5.2
#              format + PICO-8 opcode extensions) to file/stdout
# native-run — run a script with a 32 KiB RAM image preloaded as the
#              interpreter's PICO-8 memory (differential diagnostics)
# diag_dump  — A/B luaL_loadfilex vs luaL_loadbufferx dump determinism

ALL = p8luac native-run diag_dump

all: $(ALL)

p8luac: p8luac.c ../liblua.a
	g++ -std=c++17 -O2 -Wall -I.. $< ../liblua.a -o $@ -lm

native-run: native-run.c ../liblua.a
	g++ -std=c++17 -O2 -Wall -I.. $< ../liblua.a -o $@ -lm

diag_dump: diag_dump.c ../liblua.a
	g++ -std=c++17 -O2 -Wall -I.. $< ../liblua.a -o $@ -lm

clean:
	rm -f $(ALL)

.PHONY: all clean
