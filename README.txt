=================================================

  INDECS: INdependent DEComposition of networkS

=================================================

Matlab was used to develop the function used here.
The function indepDecomp returns a nontrivial independent decomposition of a chemical reaction network (CRN), if it exists. If no such decomposition exists, a message appears saying so. Furthermore, the output variables 'model', 'R', 'G', and 'P' allows the user to  view the following, respectively:

   - Complete network with all the species listed in the 'species' field of the structure 'model'
   - Matrix of reaction vectors of the network
   - Undirected graph of R
   - Partitions representing the decomposition of the reactions



=================================
How to fill out 'model' structure
=================================

'model' is the input for the function indepDecomp. It is a structure, representing the CRN, with the following fields (the kinetics of the network is not needed):

   - id: name of the model
   - species: a list of all species in the network; this is left blank since incorporated into the function is a step which compiles all species used in the model
   - reaction: a list of all reactions in the network, each with the following subfields:
        - id: a string representing the reaction
        - reactant: has the following further subfields:
             - species: a list of strings representing the species in the reactant complex
             - stoichiometry: a list of numbers representing the stoichiometric coefficient of each species in the reactant complex (listed in the same order of the species)
        - product: has the following further subfields:
             - species: a list of strings representing the species in the product complex
             - stoichiometry: a list of numbers representing the stoichiometric coefficient of each species in the product complex (listed in the same order of the species)
        - reversible: has the value true or false indicating if the reaction is reversible or not, respectively

To fill out the 'model' structure, write a string for 'model.id': this is just to put a name to the network. To add the reactions to the network, use the function addReaction where the output is 'model'. addReaction is developed to make the input of reactions of the CRN easier than the input in [7]:

   addReaction
      - OUTPUT: Returns a structure called 'model' with added field 'reaction' with subfields 'id', 'reactant', 'product', 'reversible', and 'kinetic'. The output variable 'model' allows the user to view the network with the added reaction.
      - INPUTS
           - model: a structure, representing the CRN
           - id: visual representation of the reaction, e.g., reactant -> product (string)
           - reactant_species: species of the reactant complex (cell)
           - reactant_stoichiometry: stoichiometry of the species of the reactant complex (cell)
           - reactant_kinetic: kinetic orders of the species of the reactant complex (array)
           - product_species: species of the product complex (cell)
           - product_stoichiometry: stoichiometry of the species of the product complex (cell)
           - product_kinetic: "kinetic orders" of the species of the product complex, if the reaction is reversible (array); if the reaction in NOT reversible, leave blank
           - reversible: logical; whether the reaction is reversible or not (true or false)
      * Make sure the function addReaction is in the same folder/path being used as the current working directory.



========
Examples
========

8 examples are included in this folder, all based on [1] except Example 8 [3]:

   - Example 1: Generalized mass action model of anaerobic fermentation pathway of Saccharomyces cerevisiae

   - Example 2: A metabolic network with one positive feedforward and a negative feedback

   - Example 3: Baccam influenza virus model

   - Example 4: Baccam influenza virus model with delayed virus production

   - Example 5: Handel influenza virus model

   - Example 6: Generalized mass action model of purine metabolism in man

   - Example 7: A reaction network governed by mass action kinetics

   - Example 8: Figure 7



===================
Contact Information
===================

For questions, comments, and suggestions, feel free to contact me at pvnlubenia@yahoo.co.uk.


- Patrick Lubenia (26 August 2022)



==========
References
==========

   [1] Hernandez B, De la Cruz R (2021) Independent decompositions of chemical reaction networks. Bull Math Biol 83(76):1-23. https://doi.org/10.1007/s11538-021-00906-3

   [2] Soranzo N, Altafini C (2009) ERNEST: a toolbox for chemical reaction network theory. Bioinform 25(21):2853-2854. https://doi.org/10.1093/bioinformatics/btp513

   [3] Yu P, Craciun G (2018) Mathematical analysis of chemical reaction systems. Isr J Chem 58:1-10. https://doi.org/10.1002/ijch.201800003