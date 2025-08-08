# S7-PLC_MD5
## MD5 encryption FC for Siemens PLC S7-1200 and S7-1500

The MD5 message-digest algorithm is a widely used hash function producing a 128-bit hash value.
In this implmementation the string length is limited to a maximum length of 254 characters (String[254] - 2032 bit).

depending on the input "inputmode" different inputformats are used
	
	- 1 Message is used as Bytes
	- 2 Message is used as String

depending on the input "outputmode" different outputformats are available

	-1 The digest ouput is the final hash value as bytes of A - D (Array [0..15] of Byte)
	-2 The hexdigest output is the final hash value as a hexadecimal string of A - D (32 bytes string)
	-3 Both 1 and 2

For further informations take a look at RFC 1321.
MD5 is not considered anymore as a secure hash type!

steps:

	-Step 00: Initialize variables
	-Step 01: Convert and save message in data as Bytes
	-Step 02: Appending padding Bits 
	-Step 03: Append 64 Bit containg the original message length in Bits
	-Step 04: Get the amount of chunks data (chunk = 512 Bit)
	-FOR every chunk do Step 05 - Step 08:
	    -Step 05: Save variables for later use
	    -Step 06: Break the chunk into 16 DWords
	    -Step 07: Do some bitwise operations on the 16 chunk DWords in 64 rounds
	    -Step 08: Save the chunk's hash TO result FOR the next chunk 
	-Step 09: Produce "digest"
	-Step 10: Produce "hexdigest"

  
<img width="1284" height="598" alt="MD5" src="https://github.com/user-attachments/assets/902d03aa-cf0c-4126-b6cd-a82d9bfbc13f" />




