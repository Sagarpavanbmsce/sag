def bin2dec(val):
    dec,i=0,0
    for dig in val[::-1]:
        dec+=int(dig)*2**i
        i+=1
    return dec
val=input("Enter")
print(bin2dec(val))

class ResistanceCalculator:
    def __init__(self, voltage, current):
        self.voltage = voltage
        self.current = current

    def calculate_resistance(self):
        if self.current != 0:
            return self.voltage / self.current
        else:
            return float('inf')


class InductanceCalculator(ResistanceCalculator):
    def __init__(self, voltage, current):
        super().__init__(voltage, current)

    def calculate_inductance(self, frequency):
        if self.current != 0 and frequency != 0:
            return self.voltage / (2 * 3.14159 * frequency * self.current)
        else:
            return float('inf')


class CapacitanceCalculator(ResistanceCalculator):
    def __init__(self, voltage, current):
        super().__init__(voltage, current)

    def calculate_capacitance(self, frequency):
        if self.current != 0 and frequency != 0:
            return self.current / (2 * 3.14159 * frequency * self.voltage)
        else:
            return float('inf')


# Usage example:
voltage_value = 220  # Volts
current_value = 0.1  # Amperes
frequency_value = 50  # Hertz

# Calculate resistance
resistance_calculator = ResistanceCalculator(voltage_value, current_value)
resistance_result = resistance_calculator.calculate_resistance()
print("Resistance:", resistance_result, "ohms")

# Calculate inductance
inductance_calculator = InductanceCalculator(voltage_value, current_value)
inductance_result = inductance_calculator.calculate_inductance(frequency_value)
print("Inductance:", inductance_result, "Henries")

# Calculate capacitance
capacitance_calculator = CapacitanceCalculator(voltage_value, current_value)
capacitance_result = capacitance_calculator.calculate_capacitance(frequency_value)
print("Capacitance:", capacitance_result, "Farads")

