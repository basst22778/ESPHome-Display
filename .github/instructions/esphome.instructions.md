---
name: esphome-config
description: "Use when: working with ESPHome YAML configuration (*.yaml, *.yml). Applies patterns for YAML structure, Home Assistant integration, and ESP32 device management."
applyTo: "esp32*.yaml"
---

# ESPHome Configuration Guidelines

## YAML Structure & Formatting

- **Indentation**: Use 2 spaces (never tabs)
- **Sections**: Organize in logical order: `esphome` → hardware (`esp32`, `psram`) → core services (`logger`, `api`, `ota`) → components → Home Assistant integration
- **Comments**: Use `# ---` dividers to separate major sections; add inline comments for non-obvious settings
- **Keys**: Use lowercase with underscores; maintain consistency with ESPHome documentation
- **Lists**: Use `-` on separate lines (not inline); indent consistently

## Home Assistant Integration

- **API Encryption**: Always include encryption key in `api:` block for secure communication
- **Device Naming**: Set both `name` and `friendly_name` in `esphome:` block for clear identification in Home Assistant
- **OTA Updates**: Always enable OTA without password (Home Assistant manages authentication)
- **Native API**: Use Home Assistant's native API instead of MQTT when possible for better integration and reliability

## ESP32 Configuration

- **Framework**: Specify `esp-idf` for better performance and component support
- **PSRAM**: Enable PSRAM if using displays, custom fonts, or graphics buffers
- **Board**: Declare the specific board model (e.g., `lolin_s2_mini`) for correct pin mappings

## Component Organization

- Group related components together
- Include comments describing component purpose (sensors, automations, displays, etc.)
- When adding new components, include both configuration AND Home Assistant service/entity setup

## Code Review Checklist

When writing ESPHome configs:
- [ ] All section headers are commented and properly separated
- [ ] Indentation is consistent (2 spaces)
- [ ] API encryption key is present and non-trivial
- [ ] PSRAM enabled if display/graphics components present
- [ ] Component sections are organized logically
- [ ] Device names are set for Home Assistant discoverability
