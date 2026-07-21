# MOKOLA-VIRUS-ALPHAFOLD-ANALYSIS
This was a hands-on structural biology project on demonstrating AlphaFold2 protein structure prediction, domain interpretation, and confidence metric analysis using a Mokola virus protein model.

Introduction
Advancements in computational biology have significantly transformed how we study protein structures. Among these tools, AlphaFold has emerged as a powerful system for predicting protein 3D structures with remarkable accuracy.

During a hands-on workshop on AlphaFold in biologics development by Helix Biogen Institute , I carried out a structural prediction and analysis of a protein from the Mokola virus. Beyond generating the structure, the focus of this work was to interpret the confidence metrics provided by AlphaFold2, particularly Predicted Local Distance Difference Test (pLDDT), Predicted Aligned Error (PAE) and Multiple Sequence Alignment (MSA) coverage

This article summarizes the structural insights obtained from that analysis. For any Alphafold2 result to be interpreted meaningfully, these questions must be satisfactorily answered ;

where are the protein domains?
are they rigidly connected together?
which parts of the protein are usable for downstream analyses?
what is the biological implication of answers to Qn.1, Qn.2 and Qn.3

Method Overview
The workflow followed included: Retrieval of protein sequence data from NCBI, Structure prediction using AlphaFold, Visualization and inspection of 3D structure using PyMOL and lastly Interpretation of output confidence metrics (pLDDT, PAE, and MSA coverage)

pLDDT Analysis: Local Confidence Across the Protein
The pLDDT score provides residue-level confidence in the predicted structure. with a maximum possible score being 100 on Y-axis. the X-axis has positions/residues.

Article content
pLDDT Plot [percentage confidence predicted(Y-axis) plotted against residual positions(X-axis)]
Residues 1–45 show Low confidence (pLDDT < 50), suggesting a likely disordered or flexible N-terminal region. Residues ~50–120 exhibit a High confidence plateau (pLDDT ~70–80) indicating a well-defined structural domain (DOMAIN 1). Residues 120–130 show a noticeable drop in confidence, consistent with a flexible linker region Residues 130–160 show very high confidence (pLDDT ~80–90) representing a second stable domain(DOMAIN 2). Residues 165–210: Decline in confidence suggesting a disordered C-terminal tail

These observations suggest that the protein is composed of two structured domains connected by a flexible linker, with disordered terminal regions.

PAE Analysis: Inter-domain Relationships
The Predicted Aligned Error (PAE) provides insight into the relative positioning of residues and domains. measured in Angstroms(A) and scales from dark blue(zero error) to dark red(30A). emphasis should be put on Rank 1 heat-map, the others through rank 5 are for assessing consistence in results.

Article content
PAE 2D Heat-map
The PAE heatmap Rank1 revealed two distinct low-error (blue) blocks along the diagonal, corresponding to:Domain 1 (~50–120) Domain 2 (~130–160), An elevated error between these regions indicating uncertainty in their relative orientation

This suggests that while each domain is structurally reliable, their spatial arrangement is flexible rather than fixed.

Comparison across multiple ranked models (rank2, rank3, rank4 and rank5) showed consistent patterns, reinforcing that this flexibility is likely an intrinsic property of the protein rather than a prediction artifact.

MSA Coverage: Evolutionary Support
Multiple Sequence Alignment (MSA) coverage reflects the depth of evolutionary information supporting each residue.

Article content
Sequence coverage plot
Key observations include, High sequence coverage across domain regions (~50–160) suggestive of a strong evolutionary conservation and structural reliability. The Reduced coverage toward terminal regions is consistent with low pLDDT and predicted disorder in these regions. This alignment between MSA depth and structural confidence strengthens the reliability of the predicted domains.

Integrated Structural Interpretation
Combining all three analyses:

The protein contains two well-defined structural domains (identifying these is crucial, they are the regions where active sites are and the most reliable regions for downstream analyses like molecular docking)
These domains are connected by a flexible linker region (gives insights on varried spacial conformation of the whole protein molecule)
Terminal regions are likely intrinsically disordered 
The relative orientation between domains is uncertain, suggesting potential conformational flexibility

Biological Implications
The presence of multiple domains connected by a flexible linker suggests potential domain independence in function, possible conformational changes during activity and flexibility that may influence interaction with host or viral components.

Such structural features are common in viral proteins that require adaptability for binding and function.

AFTER ALL THAT BRIEFING, I AM SURE YOU CAN TELL THE 2 DOMAINS, LINKERS, N-TERMINUS AND C-TERMINUS FROM THIS 3D STRUCTURE OF THE PROTEIN DISCUSSED

this is a PyMol export which i did not color based on confidence. but to give you a clear picture, alphafold gives it by default in shades of blue(very high confidence), yellow(low confidence) and red/orange(very low confidence)

Article content
The 3D structure render of Mokola virus protein from PyMol
Conclusion
This analysis demonstrates how AlphaFold2 outputs can be used not only to predict structures but to extract meaningful biological insights. By integrating multiple confidence metrics, it is possible to distinguish between rigid domains and flexible regions, ultimately leading to a more accurate understanding of protein behavior.

Author’s Note
This work is part of my growing exploration into computational structural biology, with a focus on applying these tools to biologically and clinically relevant systems. i herewith acknowledge my mentors Robert Kinobe, Joash Okoboi my undergrad lecturers in biochemistry and Dr. Oladipo Elijah Kolawole (Ph.D) whom i have seen here and whose works i always look up to
