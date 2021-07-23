![CDL 2020 Cohort Project](../figures/CDL_logo.jpg)
## Project 3: VQE: Constructing potential energy surfaces for small molecules

On the following we will show our results for the LiH and N2 molecules while addressing the questions presented in [instructions.pdf](https://github.com/CDL-Quantum/CohortProject_2021/tree/main/Week3_VQE/Instructions.pdf).

### Generating PES using classical methods

To begin with, we will give a brief description of the classical methods we used.

The **Hartree-Fock method (HF)** consists in representing the wavefunction of the system as a single anti-symmetrized product of one-electron functions, known as a Slater determinant. In this scheme, the molecular orbitals are expressed as a linear combination of atomic orbital functions. The combination coefficients are then optimized by a self-consistent variational procedure in which each particle is made to interact with the average density of the other particles. The output of this calculation provides a mean-field approximation to the molecular wavefunction. 

Unfortunately, HF is incapable of approximating the electron correlation effects, which are essential for computing energies within or close to chemical accuracy. To correct for this problem, one can expand the wavefunction as a superposition of all the determinants in the electron Fock space. The coefficients in the expansion can be parametrized in different ways; two popular parametrizations are the configuration interaction (CI) and the coupled-cluster (CC) methods.

In the full configuration interaction (FCI) approach, which is exact within a given basis, the wavefunction is expanded as a linear combination of all the determinants in the Fock space. The coefficients of the expansion can be solved for by variational minimization of the energy, providing the exact wavefunction for a given orbital basis.

Due to the factorial dependence on the number of determinants N related to the total number of spin orbitals, FCI becomes rapidly intractable classically. As a solution to this problem, one can truncate the CI expansion to include only determinants with a fixed number of excitations with respect to a reference configuration (usually-chosen reference: Hartree-Fock state). This idea can be formalized by defining the excitation operator T as a sum of different n-tuple excitation operators:
![excitation ops](https://latex.codecogs.com/gif.image?%5Cdpi%7B110%7D%20T=%5Csum_%7Bi=1%7D%5E%7Bn%7D%20T_i%5Ctext%7B,%20where%20%7DT_1=%5Csum_%7Bib%7Dt%5Ei_b%20a%5E%5Cdagger_a%20a_i,%5C:%5C:%20T_2=%5Csum_%7Bijbc%7Dt_%7Bbc%7D%5E%7Bij%7Da%5E%5Cdagger_%7Bb%7Da%5E%5Cdagger_c%20a_i%20a_j%5Ctext%7B,%20etc.%7D)

Tractable classical CI truncation is generally limited to single and double excitation operators, which define the **configuration interaction singles and doubles method (CISD)**.
  
The wavefunction of the **coupled-cluster (CC) method** is written as an exponential ansatz

![CC ansatz](https://latex.codecogs.com/gif.image?%5Cdpi%7B110%7D%20%5Cleft%7C%5Cpsi%20%5Cright.%20%5Crangle=e%5E%7BT%7D%20%5Cleft%7CHF%20%5Cright.%20%5Crangle)

In the method known as coupled cluster singles and doubles (CCSD), one truncates T and only considers single and double excitations. Its conventional implementation, employing the similarity-transformed Hamiltonian, is not variational.


*Advantages:*
- Variational methods can be applied in certain cases to calculations of excited states by adding a penalty term to the expectation value of H and minimizing this sum.
- Useful to solve the electronic Schrödinger equation for many-electron systems, giving accurate approximate solutions.

Variational methods are likely to **fail** for transition states or near dissociation limits of multiple bonds.

Here are the results for the LiH and N2 molecules using [this Python notebook](./S1_Classical_Methods.ipynb).

### Generating the qubit Hamiltonian

### Unitary transformations

### Hamiltonian measurements

### Use of quantum hardware


### Business Application
For each week, your team is asked to complete a Business Application. Questions you will be asked are:

* Explain to a layperson the technical problem you solved in this exercise.
* Explain or provide examples of the types of real-world problems this solution can solve.
* Identify at least one potential customer for this solution - ie: a business who has this problem and would consider paying to have this problem solved.
* Prepare a 90 second video explaining the value proposition of your innovation to this potential customer in non-technical language.

For more details refer to the [Business Application found here](./Business_Application.md)



## References
- J. Romero et at. *"Strategies for quantum computing molecular energies using the unitary coupled cluster ansatz"*. https://arxiv.org/pdf/1701.02691.pdf
