# M0dBu5

## Description

We intercepted a communication from a Modbus master to a slave on the RS485 bus as given below. Your goal, is to craft a response packet as the slave with 73(decimal) as slave data.

Master requirements are 05-02-00-00-00-01-85-BD.

Flag format: flag{XX-XX-XX-XX-XX-XX} or flag{XX-XX-XX-XX-XX-XX-XX}

## Solution

1. According to the modbus documentation, we can understand the given data:
```
05-02-00-00-00-01-85-BD
05 is the slave number
02 is the function, and here it's Read Holding Register
00 00 is the register number offset, 00 00 is counting from register 0
00 01 is the number of register read, incrementally from the offset
85 BD is the two CRC
```
2. Similarly, the slave's answer would be:
```
05-02-02-00-49-89-8E
05 is slave number
02 function
02 is the byte, per register holding 2 bytes
00 49 is the actual data, 73 in decimal
89 8E is two CRC
```

To calculate the CRC you can use online tools like: https://crccalc.com/

OR

You can use the below script:
```python
def ModRTU_CRC(buf):
    crc = 0xFFFF

    for byte in buf:
        crc ^= byte
        for _ in range(8):
            if crc & 0x0001:
                crc >>= 1
                crc ^= 0xA001
            else:
                crc >>= 1

    return crc

if __name__ == "__main__":
    user_input = input("Enter the buffer in the format xx-xx-xx-...: ")
    buf = [int(byte, 16) for byte in user_input.split('-')]
    crc = ModRTU_CRC(buf)
    print("crc: {:02X} {:02X}".format(crc & 0xFF, (crc >> 8) & 0xFF))

```

## Flag

flag{05-02-02-00-49-89-8E}