# Federated Learning for IoT Intrusion Detection

This project implements a federated learning system for intrusion detection in IoT networks using the Flower framework. The system achieves high accuracy in detecting network intrusions while preserving data privacy across edge deviceshrough federated learning.

## Project Architecture
```
├── data_processing/
│   ├── Global_Data_Processing.ipynb     # Global data processing pipeline
│   └── Combine_Processed_Data.ipynb     # Combines processed sensor datasets
├── socket_connection/
│   ├── server_script/
│   │   └── server.py                    # FL server implementation
│   └── training_script/
│       └── client.py                    # FL client with LeNet architecture
└── ssl_certificate/                     # SSL certificates for secure communication
```

## Dataset

This project uses the [ToN-IoT dataset](https://paperswithcode.com/dataset/ton-iot), a comprehensive collection of IoT network traffic and system events that include:
- Network traffic from 7 different IoT sensors
- System logs and events
- Normal and attack traffic patterns
- Multiple attack scenarios and types

The dataset includes data from multiple sensors:
- Fridge Sensor
- Garage Door Sensor
- GPS Tracker
- Modbus Sensor
- Motion Light Sensor
- Thermostat Sensor
- Weather Sensor

## Key Features

- **Federated Learning Implementation**: Using Flower framework for distributed training
- **LeNet Architecture**: Modified for intrusion detection
- **High Accuracy**: Achieved 85% accuracy in intrusion detection
- **Privacy Preservation**: Data remains local to each client
- **Secure Communication**: SSL/TLS encryption for client-server communication
- **Comprehensive Data Processing**: Global sensor-data processing pipelines

## Methodology

### Data Distribution
- Combined dataset from all 7 IoT sensors was processed and merged
- The unified dataset was then sharded into 7 equal parts
- Each shard maintains the distribution of normal and attack patterns

### Experimental Setup
- **Hardware Configuration**: 
  - 7 separate computers used as federated clients
  - 1 central server coordinating the training
  - Each client running on identical hardware for consistent performance
  - Installed requirements on all 8 client and server machines

### Federated Learning Process
1. **Data Sharding**:
   - Each client receives a unique portion of the combined dataset
   - Local data never leaves the client machines
   - Shards are balanced in terms of attack/normal sample distribution

2. **Model Architecture**:
   - Modified LeNet architecture optimized for intrusion detection
   - Input layer adapted for IoT network traffic features
   - Output layer modified for binary classification (normal/attack)

3. **Training Process**:
   - Each client trains on its local shard
   - Model updates are sent to the central server
   - Server aggregates updates using FedAvg algorithm
   - Updated global model distributed back to clients
   - Process repeats for multiple rounds until convergence

4. **Secure Communication**:
   - SSL/TLS encryption for all client-server communication
   - Custom certificate implementation for secure model update transfer

## Extended Research

This project has been further developed and enhanced in our research paper:

[**"Privacy-Preserving Federated Learning-Based Intrusion Detection Technique for Cyber-Physical Systems"**](https://www.mdpi.com/2227-7390/12/20/3194)

The paper presents a more advanced version of this implementation, featuring:
- Fully decentralized architecture
- Real-time data processing capabilities
- Independent raw dataset processing
- Enhanced model performance combination techniques and model comparison
- Improved accuracy and reduced communication overhead
- Dynamic node participation handling

The paper demonstrates significant improvements in both accuracy and efficiency compared to traditional centralized approaches, while maintaining strong privacy guarantees.

## References

- [ToN-IoT Dataset](https://paperswithcode.com/dataset/ton-iot)
- [Flower Framework Documentation](https://flower.dev/)
- [LeNet Architecture](http://yann.lecun.com/exdb/lenet/)

## Citations

If you use the extended research work in your research, please cite:

```bibtex
@article{mahmud2024privacy,
  title={Privacy-Preserving Federated Learning-Based Intrusion Detection Technique for Cyber-Physical Systems},
  author={Mahmud, S.A. and Islam, N. and Islam, Z. and Rahman, Z. and Mehedi, S.T.},
  journal={Mathematics},
  volume={12},
  number={20},
  pages={3194},
  year={2024},
  publisher={MDPI},
  doi={10.3390/math12203194}
}
```

For the implementation, please cite:

```bibtex
@misc{fl-based-ids,
  author = {[Syeda Aunanya Mahmud]},
  title = {Federated Learning-based IDS},
  year = {2024},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/syeda434am/Federated-Learning-based-IDS}}
}
```

## License

This project is licensed under the Apache License 2.0 - see the LICENSE file for details.