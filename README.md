# Quos package

Quos package simplifies plotting and simulating a quantum computing circuit employing oscillatory qubits.

### To install

    pip install matplotlib
    pip install pandas
    pip install quos

### To upgrade

    pip install --upgrade quos

### Required packages

- matplotlib
- pandas

### Included def functions in **init**.py file

- Primary (most usable) functions
- qg(ssgqt): To create a plot of a quantum circuit based on a string
- qb(ssgqt): To simulate a quantum circuit and plot Bloch spheres based on a string

- Secondary (occasionally usable) functions
- qh(): To show html file of list of quantum gates included here
- qx(): To download quos.xlsm and qblo.xlsm files
- qs(xlsm='quos.xlsm', wsht='Gates'): To generate a string for a quantum circuit

- Helper (internally used) functions
- qn(nstr, tint=True): To create a number-type string into an integer or a float
- qa(sn0r, sn0i, sn1r, sn1i): To convert qubit state numbers into qubit state angles
- qp(sn0r, sn0i, sn1r, sn1i): To convert qubit state numbers into qubit state probabilities
- qm(xS, sn0r, sn0i, sn1r, sn1i): To multiply a matrix and a vector to generate a vector

### Included gates in plots and simulations

- Qubits
- 0: qubit in state 0
- 1: Qubit in state 1
- Q: Qubit in an arbitrary state specified by two angle arguments

- Individual gates without any argument
- I: Identity
- H: Hadamard
- X: (Pauli) X gate
- Y: (Pauli) Y gate
- Z: (Pauli) Z gate
- S: S (sqrt Z) phase
- T: T (Pi/8 phase gate)
- V: V (sqrt X) phase

- Individual gates with one angle argument
- Rx: Rotation around X
- Ry: Rotation around Y
- Rz: Rotation around Z
- Ph: Global phase gate
- Pp: Phase gate for second state

- Individual gates with three angle arguments
- U: Universal rotation around arbitrary axis

- Interactive gates
- C: Controls another gate: Needs affected gate
- Cd: Reverse-controls another gate: Needs affected gate
- Sw: Swaps with another gate: Needs connected Sw
- iSw: Imaginary swaps with another gate: Needs connected iSw

- Measurement related gates
- M: Measurement gate

These gates can work for qudits after some modifications.

### Example string to represemt a quantum circuit

    txt = '1,3,0|Q 30 60,5,0|H,a,1|Y,1,2|Z,2,2|X,3,2|Y,4,2|Z,5,2|X,6,2|S,2,3|T,4,3|V,6,3|'
    txt = txt + 'Rx 30,1,4|Ry 15,2,4|Rz 15,3,4|Rz 30,4,4|Ry 15,5,4|Rx 15,6,4|'
    txt = txt + 'Ph 15,2,5|Pp 30,4,5|C,2,6,C,5,6,X,3,6|Cd,1,7,Ph 15,2,7|U 30 30 15,4,7|'
    txt = txt + 'U 15 15 30,6,7|C,1,8,X,2,8|Sw,4,8,Sw,6,8|iSw,3,9,iSw,4,9|M,a,10'

- 1 (qubit 1) on qubit 3 at time 0
- Q 30 60 (qubit with angles 30 60) on qubit 5 at time 0
- 0 (qubit 0) on other qubits at time 0
- H (Hadamard gate) on all qubits at time 1
- Y (Pauli Y gate) on qubit 1 at time 2 ...
- S (S gate) on qubit 2 at time 3 ...
- Rx 30 (rotation by 30 around X) on qubit 1 at time 4 ...
- Ph 15 (global phase gate by 15) on qubit 2 at time 5
- Pp 30 (phase gate for second state by 30) on qubit 4 at time 5
- C (control points) on qubits 2 and 5 at time 6 controlling X on qubit 3
- Cd (reverse control point) on qubit 1 at time 7 controlling Ph 15 on qubit 2
- U 30 30 15 (rotation by 30 30 15 around X Y Z) on qubit 4 at time 7 ...
- C (control point) on qubit 1 at time 8 controlling X on qubit 2
- Sw (swap) on qubits 4 and 6 at time 8
- iSw (imaginary swap) on qubits 3 and 4 at time 9
- M (measurement gate) on all qubits at time 10

### Example codes using this package

    import quos

    # To show html file of list of quantum gates included here
    quos.qh()
    # To download quos.xlsm and qblo.xlsm files
    quos.qx()
    # To generate a string for a quantum circuit
    txt = quos.qs(xlsm=<Excel file path>, wsht=<spreadsheet name>)

    # To create a plot of a quantum circuit based on a string
    qg(txt)

    #To simulate a quantum circuit and plot Bloch spheres based on a string
    qb(ssgqt):

### Version History

- 0.0.1 2023-11-07 Initial release
- 0.0.2 2023-11-07 Minor corrections
- 0.0.3 2023-11-07 Minor corrections
- 0.0.4 2023-11-07 Minor corrections
- 0.0.5 2023-11-09 Removed dependancy on networkx package
- 0.0.6 2023-11-09 Enabled plotting of CNOT gate
- 0.0.7 2023-11-10 Enabled arguments and plotting of qubits
- 0.0.8 2023-11-14 Enabled several other gates
- 0.0.9 2023-11-15 Enabled measurement gates
- 0.0.10 2023-11-16 Enabled Excel file output
- 0.0.11 2023-11-20 Enabled simulation in Excel file
- 0.0.12 2023-11-29 Enabled simulation and Bloch spheres
- 0.0.13 2023-12-02 Improved simulation and Bloch spheres
- 0.0.14 2023-12-05 Improved simulation and Excel files
- 0.0.15 2023-12-06 Enabled Toffoli gates
- 0.0.16 2023-12-11 Improved Bloch sphere representations
