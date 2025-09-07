## Neuro_EEG_Control

Neuro_EEG_Control is a Python library that enables seamless communication with NeuroSky MindWave EEG headsets, allowing you to capture, process, and respond to brainwave data in real time.

This package is built on NeuroSky’s official MindWave communication protocol and has been validated with the MindWave Mobile device. It offers both callback-driven events and direct property access for EEG metrics such as attention, meditation, and frequency band power values.

## 📦 Installation

You can install the library either from PyPI or from source:

From PyPI

```pip install Neuro_EEG_Control``


From source

Download the source distribution (dist/ folder or GitHub release).

Extract the archive and navigate into the project directory.

Run:

```python setup.py install```

🚀 Quick Start
Import and Initialize
```from Neuro_EEG_Control import NeuroPy```

# Create an instance (port and baudrate can be passed if needed)
```neuropy = NeuroPy()```

Start & Stop Streaming
```neuropy.start()   # begin streaming EEG data
# ...
neuropy.stop()    # gracefully stop the connection
```
## 📊 Available EEG Data

The following variables are exposed:

Cognitive States: attention, meditation

Signal Quality: poorSignal, blinkStrength, rawValue

Frequency Bands:

delta, theta

lowAlpha, highAlpha

lowBeta, highBeta

lowGamma, midGamma

## 🖥️ Accessing Data

You can access EEG metrics in two different ways:

1. Callbacks (event-driven)
```from time import sleep

def attention_callback(value):
    print("Attention:", value)

neuropy.setCallBack("attention", attention_callback)
neuropy.start()

try:
    while True:
        sleep(0.2)
finally:
    neuropy.stop()

2. Direct Property Access (polling)
from time import sleep

neuropy.start()

while True:
    if neuropy.meditation > 70:
        print("High meditation detected, stopping...")
        neuropy.stop()
        break
    sleep(0.2)```

## ⚙️ Compatibility

Python 2.7

Python 3.x

## ⚠️ Notes

Tested with NeuroSky MindWave Mobile. Compatibility with other models may vary.

For headset model differences, refer to NeuroSky’s official documentation
.

Another third-party library exists, but it has not been tested alongside this one.

## 📚 Resources

Original developer blog post: lihashgnis.blogspot.in

## 🤝 Contributing

Contributions are welcome!

Fork the repo

Create a feature branch

Submit a pull request

