# Evaluate Quantum Fourier Transform using Quantum Machine Learning

## Introduction

Quantum Fourier Transform (QFT) is a fundamental algorithm in quantum computing, essential in various quantum algorithms, notably Shor's algorithm for integer factorization. Its power lies in transforming quantum states into their frequency domain, akin to the classical discrete Fourier Transform.

In quantum computing, the measurement basis is crucial. Commonly, the $σ_z$-basis is used, but for specific problems, other bases like the quantum Fourier basis are more appropriate. This project delves into the quantum Fourier basis, which, like its classical counterpart, represents quantum data in the frequency domain. The QFT is an operator that transitions a state vector from the $σ_z$-basis to the Fourier basis.

This project aims to train a variational quantum circuit to evaluate QFTs of state vectors, using advanced Quantum Machine Learning (QML) techniques. By leveraging quantum mechanics principles, this implementation demonstrates quantum algorithms' enhanced capabilities over classical methods in specific computational tasks.

A key component of this project is the optimization of a variational quantum circuit, initially represented by the `qft_via_qml` function, which has been modularized into three distinct functions for improved clarity and functionality. Within the employed circuit, the two qubits first undergo a transformation through a sequence of Hadamard gates to establish a superposition, followed by parameterized rotation gates $R_z(\theta)$, which are finely tuned during the optimization process. This circuit culminates with an inverse Quantum Fourier Transform (QFT), bringing the qubits from the Fourier basis back to the computational basis. This process, and its optimization, are central to our exploration of QFT's evaluation using machine learning techniques.

The circuit, parameter array, and cost array after each optimization step are critical outputs of this process. Parameters include the number of qubits (n), the training number (m), the number of iterations (steps), and the learning rate.

![](/readme_visuals/Variational_QFT_Circuit_Optimization.png)

Through this project, we explore the intersection of Quantum Computing and Machine Learning, focusing on the theoretical and practical aspects of QFT. Using tools like PennyLane, NumPy, and Matplotlib, we present a thorough analysis and implementation of Quantum Fourier Transform using Quantum Machine Learning techniques.


## Dependencies

To ensure smooth operation and replication of the project results, the following libraries and tools are required:

- **PennyLane**: A powerful library for quantum machine learning, quantum computing, and quantum chemistry. It's essential for creating and optimizing quantum circuits in our project.
- **NumPy**: A fundamental package for scientific computing in Python. The PennyLane version of NumPy is used to ensure compatibility with quantum tensors.
- **Matplotlib**: A versatile plotting library in Python, used for visualizing data and results in a professional manner.

### Installation

To install these dependencies, run the following commands in your Python environment:

```bash
pip install pennylane
pip install 'pennylane[numpy]'
pip install matplotlib
```

## Quantum Fourier Transform (QFT)

The Quantum Fourier Transform is a quantum analogue of the classical discrete Fourier Transform. It plays a crucial role in quantum computing, particularly in algorithms like Shor's algorithm for prime factorization and quantum phase estimation. 

### Theoretical Background

QFT transforms a quantum state into its frequency domain. Mathematically, it is represented as:

$$QFT|\psi\rangle = \frac{1}{\sqrt{N}} \sum_{k=0}^{N-1} e^{2\pi i jk/N} |k\rangle$$

where $|\psi\rangle$ is the input quantum state, $N$ is the dimension of the Hilbert space, and $|k\rangle$ are the computational basis states.

The power of QFT lies in its ability to perform this transformation exponentially faster than its classical counterpart, offering significant advantages in various quantum algorithms.

### Implementation in Quantum Circuits

In this project, QFT is implemented using quantum circuits that employ a series of quantum gates. The gates used include the Hadamard gate for creating superpositions and phase rotation gates for achieving the necessary transformations. The circuit design and gate sequences are optimized for efficiency and effectiveness in performing the QFT.

The implementation details and the specific quantum circuit used for the QFT in this project are thoroughly explained and visualized in the accompanying Jupyter Notebook.

## Quantum Circuit for QFT

The Quantum Circuit for the Quantum Fourier Transform (QFT) is central to our project. This section outlines its construction and functionality.

### Circuit Construction

The QFT circuit is constructed using a sequence of quantum gates. Here's a high-level overview of the process:

1. **Hadamard Gates**: Applied to each qubit, these gates create a superposition of states, laying the foundation for the Fourier Transform.
2. **Phase Rotation Gates**: These are crucial for achieving the frequency domain representation. The rotation gates are applied in a specific sequence to ensure the correct transformation.

The detailed implementation, including the precise sequence and parameters of the gates, can be found in the `QFT_with_QML.ipynb` notebook.

### Functionality and Operation

The circuit operates by transforming the input quantum state into its Fourier-transformed equivalent in the quantum domain. This transformation is characterized by the following mathematical expression:

$$|j\rangle \rightarrow \frac{1}{\sqrt{N}} \sum_{k=0}^{N-1} e^{2\pi i jk/N} |k\rangle$$

This formula reflects the change from the time domain to the frequency domain, which is the essence of the Fourier Transform, now in the quantum computing context.

The notebook provides a step-by-step guide to the circuit's operation, including visualizations of the quantum states at various stages of the transformation process. This allows for a deeper understanding of the quantum mechanics at play in the QFT.

## Optimization Function

Optimization plays a critical role in fine-tuning the parameters of the quantum circuit for effective Quantum Fourier Transform implementation. This project utilizes advanced optimization techniques to achieve the best possible results.

### RMSProp Optimizer

The RMSProp optimizer is employed for its efficiency in handling complex optimization landscapes typical in quantum circuits. It adjusts the learning rate during training, which helps in faster convergence to the optimal parameters.

The optimizer operates on the principle of minimizing the cost function, which in this context, is designed to measure the fidelity of the QFT operation. The mathematical expression for the optimization process is:

$$\theta_{new} = \theta_{old} - \eta \frac{\partial \mathcal{L}}{\partial \theta}$$

where $\theta$ represents the parameters of the circuit, $\eta$ is the learning rate, and $\mathcal{L}$ is the cost function.

### Cost Function

The cost function is specifically designed to quantify the accuracy of the QFT. It compares the output state of the circuit with the expected state, providing a measure of the performance of the circuit. The lower the cost, the higher the fidelity of the QFT operation.

### Implementation Details

The implementation of the optimization function, along with the cost function, is detailed in the `QFT_with_QML.ipynb` notebook. The notebook guides you through the optimization process, showing how the parameters evolve and how the cost function decreases over time, ensuring the optimal performance of the QFT circuit.

## Visualization

Effective visualization is key to understanding the complex dynamics of quantum circuits and the results they produce. This project employs various visualization techniques to illustrate the outcomes of the Quantum Fourier Transform.

### Plotting the Optimization Surface

One of the primary visualization techniques used is plotting the optimization surface. This involves:

- Creating a grid over a range of parameter values.
- Calculating the cost function for each point in the grid, representing the performance of the circuit at those parameters.
- Visualizing this data in a 3D plot to understand the optimization landscape.

The visualization helps in identifying the regions where the optimizer performs efficiently and the areas of parameter space where the cost function is minimized.

### Visualizing Quantum States

Another crucial aspect of visualization in this project is the representation of quantum states:

- The states before and after applying the QFT are visualized.
- The transition of states through the quantum circuit is depicted, offering insights into the workings of the QFT.

### Custom Visualization Functions

The project includes custom functions for visualizing these aspects, with detailed annotations and professional-quality plots. These functions are designed to be adaptable, allowing for different parameters and settings to be visualized effectively.

### Insights from Visualizations

Through these visualizations, the project provides a deeper understanding of:

- How the QFT transforms quantum states.
- The efficiency and effectiveness of the optimization process.
- The overall behavior and performance of the quantum circuit.

The `QFT_with_QML.ipynb` notebook contains detailed code and explanations for these visualizations, guiding you through each step of the process.


## Results and Discussion

This project's implementation of the Quantum Fourier Transform (QFT) using Quantum Machine Learning techniques has yielded insightful results, demonstrating the capabilities and potential of quantum computing in advanced computational tasks.

### Key Outcomes

- **Efficiency of QFT**: The project successfully demonstrates the efficiency of QFT in transforming quantum states into their frequency domain. This is crucial for applications in quantum algorithms and quantum computing tasks.
- **Optimization Results**: The use of the RMSProp optimizer and a carefully designed cost function has shown effective optimization of the quantum circuit parameters. The evolution of these parameters towards optimal values is a testament to the robustness of the optimization strategy.
- **Visualization Insights**: The visualizations provided clear and intuitive insights into the quantum states' transformations and the optimization process's effectiveness.

### Discussion

The implementation of QFT in a quantum machine learning context opens up new avenues for exploration in quantum computing. The project highlights:

- The potential for quantum algorithms to outperform classical counterparts in certain computational tasks.
- The importance of effective optimization and visualization techniques in understanding and harnessing the power of quantum computing.
- The project also suggests areas for future research and improvements, particularly in scaling the implementation to more complex quantum systems and exploring other quantum machine learning applications.

### Concluding Remarks

Overall, the project not only achieves its goal of evaluating QFT using Quantum Machine Learning but also provides a foundation for further exploration and research in this exciting and rapidly evolving field.

## Conclusion

The "Evaluate Quantum Fourier Transform using Quantum Machine Learning" project represents a significant step forward in the integration of quantum computing and machine learning. By successfully implementing and analyzing the Quantum Fourier Transform (QFT) within a quantum machine learning framework, this project demonstrates the profound capabilities that quantum computing brings to solving complex computational problems.

### Recap of Achievements

- **Successful Implementation of QFT**: The project effectively demonstrates the Quantum Fourier Transform's implementation, showcasing its efficiency and potential in quantum computing.
- **Advanced Optimization Techniques**: The utilization of sophisticated optimization methods, specifically the RMSProp optimizer, highlights the importance of fine-tuning quantum circuits for optimal performance.
- **Insightful Visualizations**: The project employs professional-quality visualizations to elucidate the complex dynamics of quantum states and the optimization process, making the results accessible and understandable.

### Implications and Future Directions

The findings and methodologies presented in this project pave the way for further research in quantum computing and its applications in machine learning. Future work could focus on:

- Scaling the implementation to more complex quantum systems and algorithms.
- Exploring other quantum machine learning applications and their potential impacts.
- Enhancing the optimization techniques for even more efficient quantum computations.

### Final Thoughts

In conclusion, this project not only achieves its goal of evaluating the Quantum Fourier Transform using Quantum Machine Learning but also serves as a catalyst for future explorations in this innovative and rapidly advancing field.
