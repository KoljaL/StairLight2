
╔═══════════════════════════════════════════════════════╗
║              COMMAND REFERENCE                        ║
╚═══════════════════════════════════════════════════════╝

📋 DISPLAY COMMANDS:
  h              - Show this help
  p              - Print current configuration

🎬 EFFECT TRIGGER COMMANDS:
  1              - Start Walk-Up effect
  2              - Start Walk-Down effect
  3              - Start Knight Rider effect
  0              - Stop all effects

⚙️  CONFIGURATION COMMANDS (format: command=value):
  sd=<0-1000>    - Set step delay (ms) for ALL effects
  fd=<0-2000>    - Set fade duration (ms) for ALL effects
  ov=<0-5>       - Set overlap (LEDs) for ALL effects
  br=<0-100>     - Set brightness (%) for ALL effects
  to=<0-60000>   - Set effect timeout (ms)

  sd1=<value>    - Set step delay for Walk-Up only
  sd2=<value>    - Set step delay for Walk-Down only
  sd3=<value>    - Set step delay for Walk-Up-Out only
  sd4=<value>    - Set step delay for Walk-Down-Out only

  fd1=<value>    - Set fade duration for Walk-Up only
  fd2=<value>    - Set fade duration for Walk-Down only
  fd3=<value>    - Set fade duration for Walk-Up-Out only
  fd4=<value>    - Set fade duration for Walk-Down-Out only

  ov1=<value>    - Set overlap for Walk-Up only
  ov2=<value>    - Set overlap for Walk-Down only
  ov3=<value>    - Set overlap for Walk-Up-Out only
  ov4=<value>    - Set overlap for Walk-Down-Out only

  br1=<value>    - Set brightness for Walk-Up only
  br2=<value>    - Set brightness for Walk-Down only

🎯 SENSOR CONFIGURATION:
  sens=<0.5-5.0> - Set motion sensitivity (m/s²)
  deb=<100-1000> - Set debounce delay (ms)

💾 STORAGE COMMANDS:
  s              - Save current config to EEPROM
  l              - Load config from EEPROM
  r              - Reset to factory defaults

Examples:
  sd=200         - Set ALL effects step delay to 200ms
  br=75          - Set ALL effects brightness to 75%
  sd1=150        - Set Walk-Up step delay to 150ms
  fd2=600        - Set Walk-Down fade to 600ms
  sens=2.0       - Set motion sensitivity to 2.0 m/s²
  deb=300        - Set debounce delay to 300ms



╔═══════════════════════════════════════════════════════╗
║           CURRENT CONFIGURATION                       ║
╚═══════════════════════════════════════════════════════╝

🔼 WALK-UP EFFECT:
  Step Delay:     100 ms
  Fade Duration:  500 ms
  Brightness:     70 %
  Overlap:        3 LEDs
  Enabled:        YES

🔽 WALK-DOWN EFFECT:
  Step Delay:     100 ms
  Fade Duration:  500 ms
  Brightness:     70 %
  Overlap:        3 LEDs
  Enabled:        YES

⬆️  WALK-UP-OUT EFFECT:
  Step Delay:     100 ms
  Fade Duration:  500 ms
  Overlap:        2 LEDs
  Enabled:        YES

⬇️  WALK-DOWN-OUT EFFECT:
  Step Delay:     100 ms
  Fade Duration:  500 ms
  Overlap:        2 LEDs
  Enabled:        YES

⚙️  GLOBAL SETTINGS:
  Effect Timeout: 8000 ms
  Global Bright:  80 %

🎯 MOTION SENSOR:
  Sensitivity:    0.50 m/s²
  Debounce:       1000 ms

> 