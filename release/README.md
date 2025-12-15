# Telnet Client for MIPSEL 32-bit Platform

## Build Information

- **Architecture**: MIPSEL 32-bit (MIPS32 Release 2, Little Endian)
- **Linking**: Static (no dynamic dependencies)
- **Source**: GNU inetutils 2.5
- **Compiler**: GCC 12.4.0 (Ubuntu 12.4.0-2ubuntu1~24.04)
- **Build Date**: 2025-12-15

## Files

- `telnet-mipsel`: Statically linked telnet client binary for MIPSEL 32-bit
- `telnet-mipsel-static.tar.gz`: Compressed archive containing the binary

## Dependencies

All dependencies are statically linked into the binary:
- GNU C Library (glibc)
- ncurses 6.4+20240113 (built from source for MIPSEL)
- libtelnet (authentication/encryption support)
- libinetutils (utility functions)
- gnulib (GNU portability library)

## Usage

1. Extract the tarball (if using compressed version):
   ```bash
   tar xzf telnet-mipsel-static.tar.gz
   ```

2. Copy the binary to your MIPSEL target device:
   ```bash
   scp telnet-mipsel user@target:/usr/local/bin/telnet
   ```

3. Make it executable (if needed):
   ```bash
   chmod +x /usr/local/bin/telnet
   ```

4. Run telnet:
   ```bash
   telnet hostname [port]
   ```

## Verification

To verify the binary architecture:
```bash
file telnet-mipsel
```

Expected output:
```
telnet-mipsel: ELF 32-bit LSB executable, MIPS, MIPS32 rel2 version 1 (SYSV), statically linked, for GNU/Linux 3.2.0, stripped
```

## Binary Information

- **Size**: ~1.1 MB (stripped)
- **Format**: ELF 32-bit LSB executable
- **Machine**: MIPS R3000 (MIPS32r2)
- **ABI**: O32
- **Static**: Yes (no dynamic library dependencies)

## Build Configuration

The binary was built with the following configuration:
- Only telnet client enabled (all other programs disabled)
- All servers disabled
- Static linking for all dependencies
- ncurses support enabled
- IPv4 and IPv6 support enabled

## Notes

- This is a standalone binary with no external dependencies
- Can run on any MIPSEL 32-bit Linux system with kernel 3.2.0 or later
- Authentication and encryption features are included but may require additional setup
- The binary uses statically compiled glibc functions for network operations (getaddrinfo, getpwnam, getpwuid)

## License

GNU inetutils is free software distributed under the GNU General Public License version 3 or later.
See COPYING file in the source distribution for details.
