# KLVSTANAGForge Pro (v1.0.0)

### MISB ST 0601, SMPTE 336M & NATO STANAG 4609 KLV Metadata Studio

---

## Overview

**KLVSTANAGForge Pro** is an engineering utility and command-line tool built for aerospace engineers, defense contractors, UAV software developers, and ISR ground station operators. It provides automated byte-level synthesis, packet dissection, 16-bit running checksum verification, and 10-point normative compliance auditing across:

- **SMPTE 336M**: Key-Length-Value (KLV) Data Encoding Protocol  
- **MISB ST 0601 (v16/v18)**: UAS Datalink Local Set  
- **NATO STANAG 4609 (Ed 3/4)**: Digital Motion Imagery Standard  
- **WGS84 Geodetic Coordinate Systems & HAE Altitude Bounds**

---

## Key Capabilities

1. **Telemetry Packet Encoder**:  
   - Generates compliant MISB ST 0601 packets starting with the 16-byte Universal Key (`06 0E 2B 34 02 0B 01 01 0E 01 03 01 01 00 00 00`).  
   - Scales platform heading (Tag 5), pitch (Tag 6), roll (Tag 7), WGS84 latitude/longitude (Tags 13/14), and altitude (Tag 15).  
   - Computes the normative 16-bit running checksum (Tag 1).  
2. **Binary Stream Dissector**:  
   - Parses raw hexadecimal byte streams from MPEG-2 Transport Stream PES packets.  
   - Extracts and verifies all airborne sensor telemetry tags.  
3. **Tactical Heads-Up Display (HUD)**:  
   - Live simulated Full-Motion Video (FMV) crosshair overlay displaying mission data, attitude, coordinates, and optical parameters.  
4. **10-Point Normative Compliance Auditor**:  
   - Automated pass/fail checks for UL keys, checksums, timestamps, attitude envelopes, and coordinate limits.  
5. **Standalone Python CLI (`klv-cli.py`)**:  
   - Headless telemetry synthesis and packet verification for CI/CD test pipelines.

---

## Getting Started

### Web Studio

Open `source-code/index.html` in any modern web browser. Operates 100% locally with zero external network dependencies.

### Command-Line Interface

\# Synthesize KLV packet

python3 build/klv-cli.py encode \--lat 34.0522 \--lon \-118.2437 \--alt 1520.0 \--heading 142.5 \--mission "ALPHA-01"

\# Decode raw hex packet

python3 build/klv-cli.py decode "060e2b34020b01010e010301010000003b0208..."

### Automated Testing

python3 test\_klv.py