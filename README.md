# QRISE2024

Although the primary purpose of the challenge was to stack error mitigation techniques, our team over-focused on implementing improvements for the QSE error mitigation technique and suffered from a lack of overall participation. Here we present an implementation of two techniques outlined in the Generalized Quantum Subspace Expansion (GSE) method for error mitigation. 

GSE involves dividing the Hilbert space of a quantum system into smaller subspaces, each representing a specific set of basis states. Within these subspaces, the system's dynamics are simulated, allowing for the evolution of the system's state over time according to quantum mechanical equations. As the simulation progresses, additional subspaces may be dynamically added to accommodate the evolving behavior of the system, providing an efficient representation of its dynamics. The GSE method is particularly useful for studying complex quantum systems in areas such as chemistry and materials science, enabling researchers to gain insights into phenomena that are difficult to explore using classical computational methods.

In the POWER SUBSPACE approach, the basis of an expanded subspace is formed via the powers of a noisy quantum state, denoted as $ρ_m$. For a system with a Hamiltonian expressed as a combination of Pauli operators $$H = \sum{a} f{a} P_{a}$$ the GSE method constructs a series of states represented as a polynomial of $ρ$, ranging up to a certain power m. This representation captures the impact of the noise through higher-order terms, thus providing a pathway to error mitigation. 

To perform error mitigation, one must compute the elements of the Hamiltonian and overlap matrices within the expanded subspace, designated as $H_{ij}$ and $S_{ij}$​​. These elements are essentially expectation values that can be obtained from quantum circuits using controlled operations and measurements. Specifically, $H_{ij}$​​ elements are associated with the energy contributions, while $S_{ij}$​ elements relate to the state overlaps.

Upon constructing the matrices $H$ and $S$, the GSE method employs these matrices to solve a generalized eigenvalue problem. The solution yields coefficients that minimize the impact of noise and provide an error-mitigated estimation of the observable of interest. By choosing the coefficients that lead to the lowest eigenvalue (for ground state estimation) or minimal variance, the method isolates the error-mitigated quantum state within the subspace. This state is then used to compute expectation values for physical observables, effectively suppressing both stochastic and coherent errors in the process.

The POWER SUBSPACE method within GSE is particularly potent because it not only offers an error-agnostic way to suppress stochastic errors exponentially but also addresses coherent errors, which may not be effectively mitigated by other methods. It provides an enhanced framework that can be robust against imperfections in noise characterization, making it highly relevant for practical quantum computing applications on NISQ devices.

In the FAULT SUBSPACE method, we expand the subspace of the ρ to capture errors arising from faulty operations or noise in the quantum hardware. In this method, the expanded subspace is formed from non-identical quantum states using different noise-levels, and the generalized eigenvalue problem is solved using the matrices $H$ and $S$, which represent the Hamiltonian and overlap matrices in the subspace, respectively. The elements of these matrices are computed by taking expectation values of the Hamiltonian over 'faulty' states, and the solution to the eigenvalue problem yields coefficients that should represent the best error-mitigated quantum state. The solution to the eigenvalue problem yields coefficients {$α_{i}$​} that best represent the error-mitigated quantum state, as formulated in the equation: $$Hα=ESα$$
And the effective density matrix for this method is represented as:
$$ρ_{EM}​= \sum_{ij}​ α_{i}∗​α_{j}​ρ(λ_{i}​ϵ)ρ(λ_{j}​ϵ)$$
This equation underscores the method's reliance on combining states altered by different error intensities to distill an error-mitigated state that reflects the ideal, noise-free computation.

Compared to the commonly known error-extrapolation method, the FAULT SUBSPACE method achieves better results due to its use of a physical density matrix corresponding to real quantum states. This means that it it is particularly suited for scenarios where noise characteristics may drift over time or are otherwise difficult to quantify accurately, and makes it more accurate compared to error-extraploation methods which rely on the assumption that noise levels can be accurately controlled and do not take into account any physical constraints. 






