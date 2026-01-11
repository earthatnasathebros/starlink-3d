# Starlink 3D Constellation Simulation

A comprehensive GMAT (General Mission Analysis Tool) simulation of a Starlink-like satellite constellation with inter-satellite communications (ICOM) capabilities.

## Project Overview

This project models a 7-satellite constellation in various orbital configurations with full inter-satellite communication links operating in the Ka-band (32 GHz). The simulations support orbital propagation, visualization, and network analysis.

## Features

### Satellite Constellation
- **7 Satellites** with configurable orbital parameters
- **Multiple Orbital Planes** with varying elevations
- **Realistic Physical Models** including mass, drag, and solar radiation pressure
- **3D Visualization** using GMAT's OrbitView

### Inter-Satellite Communications (ICOM)
- **Ka-band Transceivers** (32 GHz frequency)
- **Phased Array Antennas** (40 dBi gain per satellite)
- **Redundant Mesh Network** with 8 inter-satellite links:
  - In-plane triangular links (Sat1-Sat2-Sat3, Sat4-Sat5-Sat6)
  - Inter-plane connectivity (Sat1↔Sat4)
  - Nadir pointing link (Sat7↔Sat1)
- **1 Gbps Total Network Capacity** (1 Gbps per satellite)
- **20 dB Link Margin** for robust communication
- **QPSK Modulation** with 7/8 convolutional coding

### Orbital Characteristics
- **Altitude**: 7000 km circular orbits
- **Inclination**: Multiple planes with different inclinations
- **Propagation**: Realistic force models including Earth's gravity and drag
- **Simulation Duration**: 1 day (86400 seconds) propagation

## File Structure

```
starlink-3d/
├── icom_sat              # Inter-satellite communications configuration
├── huston                # Ground station setup and main constellation
├── starlink gmat 3d      # 3D propagation and visualization script
├── starlink gps          # GPS constellation variant
├── update                # Updated constellation model with 7 satellites
├── new internet          # Internet connectivity variant
├── sovle                 # Solver configuration for estimation
├── fast adsl             # Fast ADSL communication variant
├── starlinkasdl          # ASDL propagation model
├── cloud data            # Cloud storage integration
├── .github/
│   ├── workflows/
│   │   └── google.yml    # CI/CD workflow
│   └── dependabot.yml    # Automated dependency updates
└── README.md             # This file
```

## Communication Specifications

### Transceiver Parameters
- **Frequency**: 32 GHz (Ka-band)
- **Bandwidth**: 1 GHz per link
- **Transmit Power**: 10W per transceiver
- **Noise Temperature**: 290K
- **Required Eb/N0**: 3 dB for communication

### Antenna Characteristics
- **Type**: Phased array antenna
- **Frequency**: 32 GHz
- **Gain**: 40 dBi
- **Polarization**: Right-hand circular
- **Pattern**: Gaussian with fixed directions

### Link Budget
- **Path Loss @ 1000 km**: ~160 dB (free space)
- **TX/RX Antenna Gain**: -80 dB (combined 40 dBi each)
- **Effective Loss**: ~80 dB
- **Link Margin**: 20 dB (operational threshold)

## ISL Network Topology

The constellation forms a redundant mesh network:

```
Orbital Plane 1:          Orbital Plane 2:          Nadir Pointing:
    Sat1                      Sat4                        Sat7
   / | \                      / | \                        |
  /  |  \                    /  |  \                       |
Sat3-Sat2                  Sat6-Sat5                      Sat1
```

Inter-plane link: Sat1 ↔ Sat4
Nadir link: Sat7 ↔ Sat1

## Resources & References

### Related Videos
- [Starlink Inter-Satellite Links Explained](https://www.youtube.com/watch?v=r5uYchIJ3d4) - Technical overview of ISL technology

### GMAT Resources
- [GMAT Official Website](http://gmat.gsfc.nasa.gov/)
- [GMAT User Guide](http://gmat.sourceforge.net/docs/R2020a/GmatUsersGuide-R2020a.pdf)
- [GMAT API Reference](http://gmat.sourceforge.net/docs/R2020a/GmatAPIReference-R2020a.pdf)

### Satellite Communications
- Ka-band Inter-Satellite Links (32 GHz)
- Free-space optical communications alternative
- Laser ISL for high data rates

## Usage

### Running the Simulation

1. **Basic Constellation Propagation**:
   ```
   Open in GMAT: huston
   Execute: BeginMissionSequence
   ```

2. **With 3D Visualization**:
   ```
   Open in GMAT: starlink gmat 3d
   Execute: BeginMissionSequence
   ```

3. **With Communication Analysis**:
   The `icom_sat` module is automatically included and provides:
   - ISL link status monitoring
   - Signal strength analysis
   - Network connectivity verification

### Modifying Parameters

Edit the satellite configuration in the respective files:
- **Orbital Elements**: Lines 10-40 (position and velocity)
- **Physical Properties**: Lines 40-70 (mass, drag coefficients)
- **Communication Settings**: `icom_sat` file (transceiver parameters)

## Configuration Details

### Satellite Initial Conditions
- **Epoch**: TAI Modified Julian Date 21545
- **Coordinate System**: EarthMJ2000Eq
- **Orbital Radius**: 7000 km
- **Orbital Velocity**: 7.5 km/s

### Propagation Settings
- **Propagator**: Internal numerical integration
- **Force Model**: Central body gravity + atmospheric drag
- **Integration Step**: Automatic (GMAT default)
- **Simulation Duration**: 86,400 seconds (1 day)

## GitHub Actions

Automated workflows are configured via `.github/workflows/google.yml`:
- Dependency updates via Dependabot (weekly)
- Automated pull requests for version upgrades
- Labels and assignees for tracking

## Contributing

To add features or improvements:
1. Create a new branch for your feature
2. Make changes to GMAT scripts
3. Test with GMAT before committing
4. Push to GitHub and create a pull request

## License

This project is maintained at [earthatnasathebros/starlink-3d](https://github.com/earthatnasathebros/starlink-3d)

## Author

**Chris Russell** (earthatnasathebros)

## Acknowledgments

- NASA GMAT Development Team
- Starlink constellation architecture research
- Inter-satellite communication technology research

---

**Last Updated**: January 11, 2026
**Current Version**: With ICOM integration and Dependabot support
