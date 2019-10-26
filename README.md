# ATM90E32 Arduino Library

This library powers the [CircuitSetup Split Single Phase Energy Meter](https://github.com/CircuitSetup/Split-Single-Phase-Energy-Meter) and the 6 Channel Expandable Energy Meter. 

## Use

### Setup 
#include <ATM90E32.h>
ATM90E32 energy_meter{};

void setup() {
   energy_meter.begin(CS_pin, lineFreq, PGAGain, VoltageGain1, CurrentGainCT1, CurrentGainCT2, CurrentGainCT3);
}

### Getting Basic Power Data
A basic loop to get basic power data: 

void loop() {
    voltage1 = energy_meter.GetLineVoltageA();
    voltage2 = energy_meter.GetLineVoltageB();
    voltage3 = energy_meter.GetLineVoltageC();

    CT1 = energy_meter.GetLineCurrentA();
    CT2 = energy_meter.GetLineCurrentB();
    CT3 = energy_meter.GetLineCurrentC();
    
    watts1 = energy_meter.GetActivePowerA();
    watts2 = energy_meter.GetActivePowerB();
    watts3 = energy_meter.GetActivePowerC();
    totalWatts = energy_meter.GetTotalActivePower();
}

### Getting Metering Values
The following are other functions for other metering data that the ATM90E32 calculates.
- GetReactivePowerA()
- GetReactivePowerB()
- GetReactivePowerC()
- GetTotalReactivePower()
- GetApparentPowerA()
- GetApparentPowerB()
- GetApparentPowerC()
- GetTotalApparentPower()
- GetPowerFactorA()
- GetPowerFactorB()
- GetPowerFactorC()
- GetTotalPowerFactor()
- GetPhaseA() //phase angle
- GetPhaseB()
- GetPhaseC()
- GetFrequency() //voltage frequency
- GetTemperature() //chip temperature
- GetTotalActiveFundPower()
- GetTotalActiveHarPower()

### Getting Energy Over Time
The following functions get data from the ATM90E32 that is converted to kWh
- GetImportEnergy() //forward active energy
- GetImportReactiveEnergy()
- GetImportApparentEnergy()
- GetExportEnergy() //reverse active energy
- GetExportReactiveEnergy()

### System Status
These functions get the raw hex values from the system status registers
- GetSysStatus0()
- GetSysStatus1()
- GetMeterStatus0()
- GetMeterStatus1()

### Getting Any Other Register Value
This function takes the name of any register (defined in ATM90E32.h) and outputs the value
- GetValueRegister(registerRead)

