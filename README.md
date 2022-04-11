# Input:  Strings Genome and symbol
symbol = "A"
Genome = "AAAAGGGG"
# Output: SymbolArray(Genome, symbol)
def SymbolArray(Genome, symbol):
    array = {}
    n = len(Genome)
    ExtendedGenome = Genome + Genome[0:n//2]
    for i in range(n):
        array[i] = PatternCount(symbol, ExtendedGenome[i:i+(n//2)])
    return array    
    
# Reproduce the PatternCount function here
def PatternCount(symbol,ExtendedGenome):
    count = 0
    for i in range(0,len(ExtendedGenome)-len(symbol)+1):
        if ExtendedGenome[i:i+len(symbol)] == symbol:
            count = count+1
    return count
    
# Input:  Strings Genome and symbol
Genome = "AAAAGGGG"
symbol = "A"
# Output: FasterSymbolArray(Genome, symbol)
def FasterSymbolArray(Genome, symbol):
    array = {}
    n= len(Genome)
    ExtendedGenome = Genome + Genome[0:n//2]
    
    #look at the first half of Genome to compute first array value
    array[0] = PatternCount(symbol, Genome[0:n//2])
    
    for i in range(1, n):
        #start by setting the current array value equal to the previous array value
        array[i] = array[i - 1]
        
        #the current array value can differ from the previous a value by at most 1
        if ExtendedGenome[i - 1] == symbol:
            array[i] = array[i] - 1
        if ExtendedGenome[i + (n//2) - 1] == symbol:
            array[i] = array[i] + 1
    return array
   
# Output: The number of times Pattern appears in Text
def PatternCount(symbol, Genome):
    count = 0 # output variable
    k = len(symbol)
    n = len(Genome)
    for i in range(n - k + 1):
        if symbol[i:i+k] == Genome:
            count += 1
    return Genome.count(symbol)
     
import sys
lines = sys.stdin.read().splitlines()
print(FasterSymbolArray(lines[0],lines[1]))    
