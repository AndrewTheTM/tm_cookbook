Welcome to the group of stuff that I want to have somewhere other than stuck on a hard drive in a computer I don't own and don't want to forget about.

This is code for the Source Audio C4 Synth Pedal. This pedal is connected to my computer's USB port directly (the pedal has a standard mini USB port on it). The pedal can be controlled via Musical Instrument Digital Interface (MIDI) control codes. The table below is from the pedal's documentation. 

The idea behind this was to ultimately build a controller to recall presets via a microcontroller, like an Arduino or ESP32. I haven't done anything on that yet.


| Parameter | CC# | Value | Description | 
| -- | -- | -- | -- | 
| External Tap Tempo | 93 | 0-127 | Externally control the LFO rate | 
| External Expression Control | 100 | 0-127 | Assign parameters with Neuro Editor | 
| Engage/Bypass | 102 | 0-127 | 0-64: Bypass, 65-127: Engage | 
| Preset Recall (Off) | 103 | 0-127 | Recalls any preset in bypass | 
| Preset Recall (On) | 104 | 0-127 | Recalls any preset engaged | 
| Engage/Bypass Toggle | 105 | any |  | 