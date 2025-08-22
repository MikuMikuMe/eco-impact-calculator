# eco-impact-calculator

Certainly! Below is a complete Python program for an eco-impact calculator that analyzes energy consumption, waste production, and travel habits. The program will prompt users for relevant data and then provide insights based on their ecological footprint. It includes comments and basic error handling to ensure the program runs smoothly.

```python
import sys

def calculate_energy_impact(electricity_kwh, gas_therms):
    """
    Calculate the carbon footprint based on energy usage.
    Includes electricity (in kilowatt-hours) and natural gas (in therms).
    """
    # Average CO2 emissions factors (source: EPA)
    ELECTRICITY_CO2_FACTOR = 0.00054  # metric tons CO2 per kWh
    GAS_CO2_FACTOR = 0.0053  # metric tons CO2 per therm

    try:
        electricity_impact = electricity_kwh * ELECTRICITY_CO2_FACTOR
        gas_impact = gas_therms * GAS_CO2_FACTOR
    except TypeError:
        print("Invalid input for energy consumption. Please enter numerical values.")
        sys.exit(1)

    return electricity_impact + gas_impact

def calculate_waste_impact(waste_kg):
    """
    Calculate the carbon footprint based on waste production.
    """
    # Average CO2 emissions factor for waste (source: EPA)
    WASTE_CO2_FACTOR = 0.0017  # metric tons CO2 per kg

    try:
        waste_impact = waste_kg * WASTE_CO2_FACTOR
    except TypeError:
        print("Invalid input for waste production. Please enter a numerical value.")
        sys.exit(1)

    return waste_impact

def calculate_travel_impact(car_km, flights_hours):
    """
    Calculate the carbon footprint based on travel.
    Includes car travel (in kilometers) and flights (in hours).
    """
    # Average CO2 emissions factors
    CAR_CO2_FACTOR = 0.00021  # metric tons CO2 per kilometer
    FLIGHT_CO2_FACTOR = 0.09  # metric tons CO2 per flight hour

    try:
        car_impact = car_km * CAR_CO2_FACTOR
        flight_impact = flights_hours * FLIGHT_CO2_FACTOR
    except TypeError:
        print("Invalid input for travel measurements. Please enter numerical values.")
        sys.exit(1)

    return car_impact + flight_impact

def provide_actionable_insights(total_impact):
    """
    Provide actionable insights based on the total carbon footprint.
    """
    print("\nTotal CO2 Impact: {:.2f} metric tons".format(total_impact))
    if total_impact > 15:
        print("High Impact: Consider reducing energy consumption and optimizing travel habits.")
    elif total_impact > 10:
        print("Moderate Impact: You might want to look into more sustainable practices.")
    else:
        print("Low Impact: Great job! Keep maintaining an eco-friendly lifestyle.")

def main():
    print("Eco-Impact Calculator\n")
    try:
        electricity_kwh = float(input("Enter monthly electricity usage in kWh: "))
        gas_therms = float(input("Enter monthly natural gas usage in therms: "))
        waste_kg = float(input("Enter monthly waste production in kg: "))
        car_km = float(input("Enter total kilometers traveled by car per month: "))
        flights_hours = float(input("Enter flight hours traveled per month: "))

        energy_impact = calculate_energy_impact(electricity_kwh, gas_therms)
        waste_impact = calculate_waste_impact(waste_kg)
        travel_impact = calculate_travel_impact(car_km, flights_hours)

        total_impact = energy_impact + waste_impact + travel_impact
        provide_actionable_insights(total_impact)
        
    except ValueError:
        print("Invalid input detected. Please enter valid numerical values.")
        sys.exit(1)

if __name__ == "__main__":
    main()
```

### Key Features:
- **Error Handling**: The program uses `try` and `except` blocks to handle potential input errors (e.g., non-numeric values).
- **User Input**: Prompts the user for various data points related to energy use, waste, and travel.
- **CO2 Calculations**: Factors from credible sources (like the EPA) are leveraged to compute the ecological footprint.
- **Output Insights**: Based on the total footprint, the program provides suggestions to reduce impact.

You can extend this program by adding more detailed suggestions, integrating additional data sources, or providing a more granular analysis with extra factors.