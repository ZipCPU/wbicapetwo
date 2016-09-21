# Wishbone to ICAPE2 interface conversion

This core maps the configuration registers of a 7-series (or Spartan--6) Xilinx
part onto register addresses on a wishbone bus interface via the ICAPE2 access
port to those parts.  The big thing this captures is the timing and handshaking
required to read and write registers from the configuration interface.

As an example of what can be done, writing a ``32'h00f`` to local address ``5'h4`` sends the IPROG command to the FPGA, causing it to immediately reconfigure itself.

As another example, the warm boot start address is located in register ``5'h10``.  Writing to this address, followed by issuing the IPROG command just mentioned will cause the FPGA to configure from that warm boot start address.

For more details on the configuration interface, the registers in question, their meanings and what they do, please see the respective User's Guide.
