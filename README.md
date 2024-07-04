def convert_temp(temp, from_unit, to_unit):
  """Converts temperature from one unit to another.

  Args:
    temp: The temperature value to convert.
    from_unit: The unit of measurement of the temperature value.
      Must be one of "C" (Celsius), "F" (Fahrenheit), or "K" (Kelvin).
    to_unit: The unit of measurement to convert the temperature value to.
      Must be one of "C" (Celsius), "F" (Fahrenheit), or "K" (Kelvin).

  Returns:
    The converted temperature value.

  Raises:
    ValueError: If from_unit or to_unit is not one of "C", "F", or "K".
  """

  if from_unit == to_unit:
    return temp

  if from_unit == "C":
    if to_unit == "F":
      return temp * (9/5) + 32
    elif to_unit == "K":
      return temp + 273.15
    else:
      raise ValueError("Invalid to_unit: {}".format(to_unit))
  elif from_unit == "F":
    if to_unit == "C":
      return (temp - 32) * (5/9)
    elif to_unit == "K":
      return (temp - 32) * (5/9) + 273.15
    else:
      raise ValueError("Invalid to_unit: {}".format(to_unit))
  elif from_unit == "K":
    if to_unit == "C":
      return temp - 273.15
    elif to_unit == "F":
      return (temp - 273.15) * (9/5) + 32
    else:
      raise ValueError("Invalid to_unit: {}".format(to_unit))
  else:
    raise ValueError("Invalid from_unit: {}".format(from_unit))

# Example usage
while True:
  try:
    temp = float(input("Enter temperature: "))
    from_unit = input("Enter unit (C, F, or K): ").upper()
    to_unit = input("Enter unit to convert to (C, F, or K): ").upper()
    converted_temp = convert_temp(temp, from_unit, to_unit)
    print("The temperature in {} is {:.2f} degrees.".format(to_unit, converted_temp))
    break
  except ValueError as e:
    print(e)
