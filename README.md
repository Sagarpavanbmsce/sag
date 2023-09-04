def bin2dec(val):
    dec,i=0,0
    for dig in val[::-1]:
        dec+=int(dig)*2**i
        i+=1
    return dec
val=input("Enter")
print(bin2dec(val))
