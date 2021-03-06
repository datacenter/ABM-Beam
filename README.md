ABM-Beam
========

Active Buffer Monitoring

Python script abmBeam.py is inteded to be run on the Nexus 3548.  It sends out Active Buffer Monitoring histogram for all the ports and the buffer-blocks over UDP.

Structure of UDP Packet:

<pre>
943  Bytes	:	Total ABM Data Containing the following:
{
	20	Bytes	:	Signature "Cisco Nexus 3548 ABM"

	4	Bytes	:	MGMT IP (a.b.c.d) - 1 Byte for each octet
	{
		1	Byte	:	a
		1	Byte	:	b
		1	Byte	:	c
		1	Byte	:	d
	}

	4	Bytes	:	Epoch – Most significant bytes first - 0xABCD
	{
		1	Byte	:	D
		1	Byte	:	C
		1	Byte	:	B
		1	Byte	:	A			
	}

	864	Bytes	:	18 Bytes for each port (48 ports) containing port number and histogram
	{
		1	Byte	:	Port number
		1	Byte	:	Port speed
		16	Bytes 	:	Buffer usage histogram
	}

	17	Bytes	:	Buffer-block 1 histogram
	{
		1	Byte	:	Buffer Block #
		16	Bytes 	:	Buffer usage histogram
	}

	17	Bytes	:	Buffer-block 2 histogram
	{
		1	Byte	:	Buffer Block #
		16	Bytes 	:	Buffer usage histogram
	}

	17	Bytes	:	Buffer-block 3 histogram
	{
		1	Byte	:	Buffer Block #
		16	Bytes 	:	Buffer usage histogram
	}
}
</pre>


For more details on running Python on the Nexus Series switches:
https://github.com/datacenter/Nexus/wiki/Python-on-Nexus-3000-Series-Switches
