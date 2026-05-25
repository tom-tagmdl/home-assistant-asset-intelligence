<img width="1536" height="1024" alt="banner_dark" src="https://github.com/user-attachments/assets/b3dd3107-7fea-4daa-8ec1-8ce304e6b985" />


# Home Assistant Asset Intelligence

**A Home Assistant custom integration that introduces “Assets” as a first-class concept — enabling homes to understand, monitor, and protect what they contain.**

---

## 🏠 Concept

Home Assistant does an incredible job modeling:

- Devices  
- Entities  
- Rooms (Areas)  
- People  

…but it does not yet model:

> **What the home actually contains**

This integration introduces a new concept:

## → Assets

An **Asset** represents anything in the home:

### Device-backed assets
- Televisions (linked to media_player entities)
- Sonos speakers
- Network equipment

### Non-device assets
- Artwork
- Antiques
- Furniture
- Musical instruments

---

## 🎯 Key Design Principles

### ✅ Native to Home Assistant
- Uses **Areas (rooms)** for location  
- Uses **Labels** for classification (no duplicate schema)  

### ✅ Device-aware
Assets can optionally link to a Home Assistant device:
- Extends context (value, documentation, story)
- Does **not replace the device model**

### ✅ Single classification system
- Uses **Home Assistant Labels** as the source of truth  
- Device labels are inherited automatically  

---

## 🧠 What Makes This Different

## → Assets define their *proper operating environment*

Each asset can specify:

- Temperature range  
- Humidity range  
- Light exposure (including direct sunlight)  

---

## 🔍 What This Enables

The home can evaluate:

> “Are the current conditions appropriate for what is in this room?”

Examples:
- Artwork exposed to excessive sunlight  
- Closets running too warm for networking equipment  
- Humidity levels impacting instruments or furniture  

---

## 🧱 Architecture Overview (V1)

- Custom Home Assistant integration
- Local storage using HA-native Store (no helpers used as database)
- Attachments via Media Source (`/media`)
- Services for asset management
- Sensors for environmental risk evaluation

---

## 🗂️ Example Asset (Conceptual)

```yaml
asset:
  name: "Den Television"

  area: den

  linked_device: media_player.den_tv

  labels:
    - tv
    - electronics
    - insured

  descriptions:
    guest: "Main television in the den"
    owner: "Upgraded during remodel"
    insurance: "Samsung 75\" QLED, model XYZ"

  operating_environment:
    temperature:
      min: 50
      max: 95
    humidity:
      min: 20
      max: 80

  documents:
    - type: receipt
      uri: media-source://media_source/local/assets/den_tv/receipt.pdf
- Closets running too warm for networking equipment  

