8. ANALYZING A NETWORK
======================

.. raw:: latex

    \clearpage
    
*After a network has been suitably described, its hydraulic and water
quality behavior can be analyzed. This chapter describes how to
specify options to use in the analysis, how to run the analysis and
how to troubleshoot problems that might have occurred with the
analysis.*


-------


   
Setting Analysis Options
~~~~~~~~~~~~~~~~~~~~~~~~

  There are five categories of options that control how EPANET analyzes
  a network: Hydraulics, Quality, Reactions, Times, and Energy. To set
  any of these options:

    1. Select the Options category from the Data Browser or select
       **Project >> Analysis Options** from the menu bar.

    2. Select Hydraulics, Quality, Reactions, Times, or Energy from the
       Browser.

    3. If the Property Editor is not already visible, click the Browser’s
       Edit button |image112| (or hit the **Enter** key).

    4. Edit your option choices in the Property Editor.



  As you are editing a category of options in the Property Editor you
  can move to the next or previous category by simply hitting the
  **Page Down** or **Page Up** keys, respectively.

Hydraulic Options
------------------

   Hydraulic options control how the hydraulic computations are carried
   out. They consist of the following items:

  +-----------------------------------+-----------------------------------+
  | *Option*                          | *Description*                     |
  +===================================+===================================+
  |                                   | Units in which nodal demands and  |
  |   Flow Units                      | link flow rates are expressed.    |
  |                                   | Choosing units in gallons, cubic  |
  |                                   | feet, or acre-feet implies that   |
  |                                   | the units for all other network   |
  |                                   | quantities are Customary US.      |
  |                                   | Selecting liters or cubic meters  |
  |                                   | causes all other units to be SI   |
  |                                   | metric. Use caution when changing |
  |                                   | flow units as it might affect all |
  |                                   | other data supplied to the        |
  |                                   | project. (See Appendix A, Units   |
  |                                   | of Measurement.)                  |
  +-----------------------------------+-----------------------------------+
  | Headloss Formula                  | Formula used to compute headloss  |
  |                                   | as a function of flow rate in a   |
  |                                   | pipe. Choices are:                |
  +-----------------------------------+-----------------------------------+
  |                                   | •         Hazen-Williams          |
  +-----------------------------------+-----------------------------------+
  |                                   | •         Darcy-Weisbach          |
  +-----------------------------------+-----------------------------------+
  |                                   | •         Chezy-Manning           |
  +-----------------------------------+-----------------------------------+
  |                                   | Because each formula measures     |
  |                                   | pipe roughness differently,       |
  |                                   | switching formulas might require  |
  |                                   | that all pipe roughness           |
  |                                   | coefficients be updated.          |
  +-----------------------------------+-----------------------------------+
  | Specific Gravity                  | Ratio of the density of the fluid |
  |                                   | being modeled to that of water at |
  |                                   | 4 deg. C (unitless).              |
  +-----------------------------------+-----------------------------------+
  | Relative Viscosity                | Ratio of the kinematic viscosity  |
  |                                   | of the fluid to that of water at  |
  |                                   | 20 deg. C (1.0 centistokes or     |
  |                                   | 0.94 sq ft/day) (unitless).       |
  +-----------------------------------+-----------------------------------+
  | Maximum Trials                    | Maximum number of trials used to  |
  |                                   | solve the nonlinear equations     |
  |                                   | that govern network hydraulics at |
  |                                   | a given point in time. Suggested  |
  |                                   | value is 40.                      |
  +-----------------------------------+-----------------------------------+
  | Accuracy                          | Convergence criterion used to     |
  |                                   | signal that a solution has been   |
  |                                   | found to the nonlinear equations  |
  |                                   | that govern network hydraulics.   |
  |                                   | Trials end when the sum of all    |
  |                                   | flow changes divided by the sum   |
  |                                   | of all link flows is less than    |
  |                                   | this number. Suggested value is   |
  |                                   | 0.001.                            |
  +-----------------------------------+-----------------------------------+
  | If Unbalanced                     | Action to take if a hydraulic     |
  |                                   | solution is not found within the  |
  |                                   | maximum number of trials. Choices |
  |                                   | are STOP to stop the simulation   |
  |                                   | at this point or CONTINUE to use  |
  |                                   | another 10 trials, with no link   |
  |                                   | status changes allowed, in an     |
  |                                   | attempt to achieve convergence.   |
  +-----------------------------------+-----------------------------------+
  | Default Pattern                   | ID label of a time pattern to be  |
  |                                   | applied to demands at those       |
  |                                   | junctions where no time pattern   |
  |                                   | is specified. If no such pattern  |
  |                                   | exists then demands will not vary |
  |                                   | at these locations.               |
  +-----------------------------------+-----------------------------------+
  | Demand Multiplier                 | Global multiplier applied to all  |
  |                                   | demands to make total system      |
  |                                   | consumption vary up or down by a  |
  |                                   | fixed amount. E.g., 2.0 doubles   |
  |                                   | all demands, 0.5 halves them, and |
  |                                   | 1.0 leaves them as is.            |
  +-----------------------------------+-----------------------------------+
  | Emitter Exponent                  | Power to which pressure is raised |
  |                                   | when computing the flow through   |
  |                                   | an emitter device. The textbook   |
  |                                   | value for nozzles and sprinklers  |
  |                                   | is ½. This may not apply to pipe  |
  |                                   | leakage. Consult the discussion   |
  |                                   | of Emitters in Section 3.1 for    |
  |                                   | more details.                     |
  +-----------------------------------+-----------------------------------+
  | Status Report                     | Amount of status information to   |
  |                                   | report after an analysis is made. |
  +-----------------------------------+-----------------------------------+
  |                                   | Choices are:                      |
  +-----------------------------------+-----------------------------------+
  |                                   | •         NONE (no status         |
  |                                   | reporting)                        |
  +-----------------------------------+-----------------------------------+
  |                                   | •         YES (normal status      |
  |                                   | reporting – lists all changes in  |
  |                                   | link status throughout the        |
  |                                   | simulation )                      |
  +-----------------------------------+-----------------------------------+
  |                                   | •         FULL (full reporting –  |
  |                                   | normal reporting plus the         |
  |                                   | convergence error from each trial |
  |                                   | of the hydraulic analysis made in |
  |                                   | each time period)                 |
  +-----------------------------------+-----------------------------------+
  |                                   | Full status reporting is only     |
  |                                   | useful for debugging purposes.    |
  +-----------------------------------+-----------------------------------+

   **Note**: Choices for Hydraulic Options can also be set from the
   **Project >> Defaults** menu and saved for use with all future projects (see Section 5.2).

Water Quality Options
-----------------------

   Water Quality Options control how the water quality analysis is
   carried out. They consist of the following:

  +-----------------------------------+-----------------------------------+
  | *Option*                          | *Description*                     |
  +===================================+===================================+
  | Parameter                         | Type of water quality parameter   |
  |                                   | being modeled. Choices include:   |
  +-----------------------------------+-----------------------------------+
  |                                   | •         NONE (no quality        |
  |                                   | analysis),                        |
  +-----------------------------------+-----------------------------------+
  |                                   | •         CHEMICAL (compute       |
  |                                   | chemical concentration),          |
  +-----------------------------------+-----------------------------------+
  |                                   | •         AGE (compute water      |
  |                                   | age),                             |
  +-----------------------------------+-----------------------------------+
  |                                   | •         TRACE (trace the        |
  |                                   | percent of flow originating from  |
  |                                   | a specific node).                 |
  +-----------------------------------+-----------------------------------+
  |                                   | In lieu of CHEMICAL, you can      |
  |                                   | enter the actual name of the      |
  |                                   | chemical being modeled (e.g.,     |
  |                                   | Chlorine).                        |
  +-----------------------------------+-----------------------------------+
  | Mass Units                        | Mass units used to express        |
  |                                   | concentration. Choices are mg/L   |
  |                                   | or μg/L. Units for Age and Trace  |
  |                                   | analyses are fixed at hours and   |
  |                                   | percent, respectively.            |
  +-----------------------------------+-----------------------------------+
  | Relative Diffusivity              | Ratio of the molecular            |
  |                                   | diffusivity of the chemical being |
  |                                   | modeled to that of chlorine at 20 |
  |                                   | deg. C (0.00112 sq ft/day). Use 2 |
  |                                   | if the chemical diffuses twice as |
  |                                   | fast as chlorine, 0.5 if half as  |
  |                                   | fast, etc. Applies only when      |
  |                                   | modeling mass transfer for pipe   |
  |                                   | wall reactions. Set to zero to    |
  |                                   | ignore mass transfer effects.     |
  +-----------------------------------+-----------------------------------+
  | Trace Node                        | ID label of the node whose flow   |
  |                                   | is being traced. Applies only to  |
  |                                   | flow tracing analyses.            |
  +-----------------------------------+-----------------------------------+
  | Quality Tolerance                 | Smallest change in quality that   |
  |                                   | will cause a new parcel of water  |
  |                                   | to be created in a pipe. A        |
  |                                   | typical setting might be 0.01 for |
  |                                   | chemicals measured in mg/L as     |
  |                                   | well as water age and source      |
  |                                   | tracing.                          |
  +-----------------------------------+-----------------------------------+

   **Note**: The Quality Tolerance determines when the quality of one
   parcel of water is essentially the same as another parcel. For
   chemical analysis this might be the detection limit of the procedure
   used to measure the chemical, adjusted by a suitable factor of
   safety. Using too large a value for this tolerance might affect
   simulation accuracy. Using too small a value will affect
   computational efficiency. Some experimentation with this setting
   might be called for.

   
Reaction Options
-----------------

   Reaction Options set the types of reactions that apply to a water
   quality analysis. They include the following:


  +-----------------------------------+-----------------------------------+
  | *Option*                          | *Description*                     |
  +===================================+===================================+
  | Bulk Reaction Order               | Power to which concentration is   |
  |                                   | raised when computing a bulk flow |
  |                                   | reaction rate. Use 1 for          |
  |                                   | first-order reactions, 2 for      |
  |                                   | second-order reactions, etc. Use  |
  |                                   | any negative number for           |
  |                                   | Michaelis-Menton kinetics. If no  |
  |                                   | global or pipe-specific bulk      |
  |                                   | reaction coefficients are         |
  |                                   | assigned then this option is      |
  |                                   | ignored.                          |
  +-----------------------------------+-----------------------------------+
  | Wall Reaction Order               | Power to which concentration is   |
  |                                   | raised when computing a bulk flow |
  |                                   | reaction rate. Choices are FIRST  |
  |                                   | (1) for first-order reactions or  |
  |                                   | ZERO (0) for constant rate        |
  |                                   | reactions. If no global or        |
  |                                   | pipe-specific wall reaction       |
  |                                   | coefficients are assigned then    |
  |                                   | this option is ignored.           |
  +-----------------------------------+-----------------------------------+
  | Global Bulk Coefficient           | Default bulk reaction rate        |
  |                                   | coefficient (K:sub:`b`) assigned  |
  |                                   | to all pipes. This global         |
  |                                   | coefficient can be overridden by  |
  |                                   | editing this property for         |
  |                                   | specific pipes. Use a positive    |
  |                                   | number for growth, a negative     |
  |                                   | number for decay, or 0 if no bulk |
  |                                   | reaction occurs. Units are        |
  |                                   | concentration raised to the (1-n) |
  |                                   | power divided by days, where n is |
  |                                   | the bulk reaction order.          |
  +-----------------------------------+-----------------------------------+
  | Global Wall Coefficient           | Wall reaction rate coefficient    |
  |                                   | (K:sub:`w`) assigned to all       |
  |                                   | pipes. Can be overridden by       |
  |                                   | editing this property for         |
  |                                   | specific pipes. Use a positive    |
  |                                   | number for growth, a negative     |
  |                                   | number for decay, or 0 if no wall |
  |                                   | reaction occurs. Units are ft/day |
  |                                   | (US) or m/day (SI) for            |
  |                                   | first-order reactions and mass/sq |
  |                                   | ft/day (US) or mass/sq m/day (SI) |
  |                                   | for zero- order reactions.        |
  +-----------------------------------+-----------------------------------+
  | Limiting Concentration            | Maximum concentration that a      |
  |                                   | substance can grow to or minimum  |
  |                                   | value it can decay to. Bulk       |
  |                                   | reaction rates will be            |
  |                                   | proportional to the difference    |
  |                                   | between the current concentration |
  |                                   | and this value. See discussion of |
  |                                   | Bulk Reactions in Section 3.4 for |
  |                                   | more details. Set to zero if not  |
  |                                   | applicable.                       |
  +-----------------------------------+-----------------------------------+
  | Wall Coefficient Correlation      | Factor correlating wall reaction  |
  |                                   | coefficient to pipe roughness.    |
  |                                   | See discussion of Wall Reactions  |
  |                                   | in Section 3.4 for more details.  |
  |                                   | Set to zero if not applicable.    |
  +-----------------------------------+-----------------------------------+

   
Times Options
-----------------

   Times options set values for the various time steps used in an
   extended period simulation. These are listed below (times can be
   entered as decimal hours or in hours:minutes notation):


  +-----------------------------------+-----------------------------------+
  | *Option*                          | *Description*                     |
  +===================================+===================================+
  | Total Duration                    | Total length of a simulation in   |
  |                                   | hours. Use 0 to run a single      |
  |                                   | period (snapshot) hydraulic       |
  |                                   | analysis.                         |
  +-----------------------------------+-----------------------------------+
  | Hydraulic Time Step               | Time interval between             |
  |                                   | re-computation of system          |
  |                                   | hydraulics. Normal default is 1   |
  |                                   | hour.                             |
  +-----------------------------------+-----------------------------------+
  | Quality Time Step                 | Time interval between routing of  |
  |                                   | water quality constituent. Normal |
  |                                   | default is 5 minutes (0:05        |
  |                                   | hours).                           |
  +-----------------------------------+-----------------------------------+
  | Pattern Time Step                 | Time interval used with all time  |
  |                                   | patterns. Normal default is 1     |
  |                                   | hour.                             |
  +-----------------------------------+-----------------------------------+
  | Pattern Start Time                | Hours into all time patterns at   |
  |                                   | which the simulation begins       |
  |                                   | (e.g., a value of 2 means that    |
  |                                   | the simulation begins with all    |
  |                                   | time patterns starting at their   |
  |                                   | second hour). Normal default is   |
  |                                   | 0.                                |
  +-----------------------------------+-----------------------------------+
  | Reporting Time Step               | Time interval between times at    |
  |                                   | which computed results are        |
  |                                   | reported. Normal default is 1     |
  |                                   | hour.                             |
  +-----------------------------------+-----------------------------------+
  | Report Start Time                 | Hours into simulation at which    |
  |                                   | computed results begin to be      |
  |                                   | reported. Normal default is 0.    |
  +-----------------------------------+-----------------------------------+
  | Starting Time of Day              | Clock time (e.g., 7:30 am, 10:00  |
  |                                   | pm) at which simulation begins.   |
  |                                   | Default is 12:00 am (midnight).   |
  +-----------------------------------+-----------------------------------+
  | Statistic                         | Type of statistical processing    |
  |                                   | used to summarize the results of  |
  |                                   | an extended period simulation.    |
  |                                   | Choices are:                      |
  +-----------------------------------+-----------------------------------+
  |                                   | •         NONE (results reported  |
  |                                   | at each reporting time step)      |
  +-----------------------------------+-----------------------------------+
  |                                   | •         AVERAGE (time-averaged  |
  |                                   | results reported)                 |
  +-----------------------------------+-----------------------------------+
  |                                   | •         MINIMUM (minimum value  |
  |                                   | results reported)                 |
  +-----------------------------------+-----------------------------------+
  |                                   | •         MAXIMUM (maximum value  |
  |                                   | results reported)                 |
  +-----------------------------------+-----------------------------------+
  |                                   | •         RANGE (difference       |
  |                                   | between maximum and minimum       |
  |                                   | results reported)                 |
  +-----------------------------------+-----------------------------------+
  |                                   | Statistical processing is applied |
  |                                   | to all node and link results      |
  |                                   | obtained between the Report Start |
  |                                   | Time and the Total Duration.      |
  +-----------------------------------+-----------------------------------+

   **Note:** To run a single-period hydraulic analyses (also called a
   snapshot analysis) enter 0 for Total Duration. In this case entries
   for all of the other time options, with the exception of Starting
   Time of Day, are not used. Water quality analyses always require that
   a non-zero Total Duration be specified.


Energy Options
-----------------

   Energy Analysis Options provide default values used to compute
   pumping energy and cost when no specific energy parameters are
   assigned to a given pump. They consist of the following:


  +-----------------------------------+-----------------------------------+
  | *Option*                          | *Description*                     |
  +===================================+===================================+
  | Pump Efficiency (%)               | Default pump efficiency.          |
  +-----------------------------------+-----------------------------------+
  | Energy Price per Kwh              | Price of energy per               |
  |                                   | kilowatt-hour. Monetary units are |
  |                                   | not explicitly represented.       |
  +-----------------------------------+-----------------------------------+
  | Price Pattern                     | ID label of a time pattern used   |
  |                                   | to represent variations in energy |
  |                                   | price with time. Leave blank if   |
  |                                   | not applicable.                   |
  +-----------------------------------+-----------------------------------+
  | Demand Charge                     | Additional energy charge per      |
  |                                   | maximum kilowatt usage.           |
  +-----------------------------------+-----------------------------------+


Running an Analysis
~~~~~~~~~~~~~~~~~~~

  To run a hydraulic/water quality analysis:

    1. Select **Project >> Run Analysis** or click |image113| on the
       Standard Toolbar.

    2. The progress of the analysis will be displayed in a Run Status
       window.

    3. Click **OK** when the analysis ends.

    

  If the analysis runs successfully the |image114| icon will appear in
  the Run Status section of the Status Bar at the bottom of the EPANET
  workspace. Any error or warning messages will appear in a Status
  Report window. If you edit the properties of the network after a
  successful run has been made, the faucet icon changes to a broken
  faucet indicating that the current computed results no longer apply
  to the modified network.

  
Troubleshooting Results
~~~~~~~~~~~~~~~~~~~~~~~

EPANET will issue specific Error and Warning messages when problems
are encountered in running a hydraulic/water quality analysis (see
Appendix B for a complete listing). The most common problems are
discussed below.

Pumps Cannot Deliver Flow or Head
-----------------------------------


   EPANET will issue a warning message when a pump is asked to operate
   outside the range of its pump curve. If the pump is required to
   deliver more head than its shutoff head, EPANET will close the pump
   down. This might lead to portions of the network becoming
   disconnected from any source of water.

Network is Disconnected
--------------------------------


   EPANET classifies a network as being disconnected if there is no way
   to provide water to all nodes that have demands. This can occur if
   there is no path of open links between a junction with demand and
   either a reservoir, a tank, or a junction with a negative demand. If
   the problem is caused by a closed link EPANET will still compute a
   hydraulic solution (probably with extremely large negative pressures)
   and attempt to identify the problem link in its Status Report. If no
   connecting link(s) exist EPANET will be unable to solve the hydraulic
   equations for flows and pressures and will return an Error 110
   message when an analysis is made. Under an extended period simulation
   it is possible for nodes to become disconnected as links change
   status over time.

Negative Pressures Exist
--------------------------------


   EPANET will issue a warning message when it encounters negative
   pressures at junctions that have positive demands. This usually
   indicates that there is some problem with the way the network has
   been designed or operated. Negative pressures can occur when portions
   of the network can only receive water through links that have been
   closed off. In such cases an additional warning message about the
   network being disconnected is also issued.

System Unbalanced
--------------------------------
  

   A System Unbalanced condition can occur when EPANET cannot converge
   to a hydraulic solution in some time period within its allowed
   maximum number of trials. This situation can occur when valves,
   pumps, or pipelines keep switching their status from one trial to the
   next as the search for a hydraulic solution proceeds. For example,
   the pressure limits that control the status of a pump may be set too
   close together. Or a pump's head curve might be too flat causing it
   to keep shutting on and off.

   To eliminate the unbalanced condition one can try to increase the
   allowed maximum number of trials or loosen the convergence accuracy
   requirement. Both of these parameters are set with the project’s
   Hydraulic Options. If the unbalanced condition persists, then another
   hydraulic option, labeled “If Unbalanced”, offers two ways to handle
   it. One is to terminate the entire analysis once the condition is
   encountered. The other is to continue seeking a hydraulic solution
   for another 10 trials with the status of all links frozen to their
   current values. If convergence is achieved then a warning message is
   issued about the system possibly being unstable. If convergence is
   not achieved then a “System Unbalanced” warning message is issued. In
   either case, the analysis will proceed to the next time period.

   If an analysis in a given time period ends with the system unbalanced
   then the user should recognize that the hydraulic results produced
   for this time period are inaccurate. Depending on circumstances, such
   as errors in flows into or out of storage tanks, this might affect
   the accuracy of results in all future periods as well.

Hydraulic Equations Unsolvable
--------------------------------

   Error 110 is issued if at some point in an analysis the set of
   equations that model flow and energy balance in the network cannot be
   solved. This can occur when some portion of a system demands water
   but has no links physically connecting it to any source of water. In
   such a case EPANET will also issue warning messages about nodes being
   disconnected. The equations might also be unsolvable if unrealistic
   numbers were used for certain network properties.

.. |image0| image:: .\/media/image1.jpeg
.. |image1| image:: .\/media/image2.png
.. |image2| image:: .\/media/image3.png
.. |image3| image:: .\/media/image4.png
.. |image4| image:: .\/media/image5.png
.. |image5| image:: .\/media/image6.png
.. |image6| image:: .\/media/image7.png
.. |image7| image:: .\/media/image8.png
.. |image8| image:: .\/media/image9.png
.. |image9| image:: .\/media/image10.png
.. |image10| image:: .\/media/image11.png
.. |image11| image:: .\/media/image12.png
.. |image12| image:: .\/media/image13.png
.. |image13| image:: .\/media/image12.png
.. |image14| image:: .\/media/image14.jpeg
.. |image15| image:: .\/media/image15.png
.. |image16| image:: .\/media/image16.jpeg
.. |image17| image:: .\/media/image17.png
.. |image18| image:: .\/media/image18.png
.. |image19| image:: .\/media/image19.png
.. |image20| image:: .\/media/image20.png
.. |image21| image:: .\/media/image21.png
.. |image22| image:: .\/media/image16.jpeg
.. |image23| image:: .\/media/image22.png
.. |image24| image:: .\/media/image18.png
.. |image25| image:: .\/media/image23.png
.. |image26| image:: .\/media/image24.png
.. |image27| image:: .\/media/image25.png
.. |image28| image:: .\/media/image26.png
.. |image29| image:: .\/media/image27.png
.. |image30| image:: .\/media/image28.png
.. |image31| image:: .\/media/image29.png
.. |image32| image:: .\/media/image30.png
.. |image33| image:: .\/media/image31.png
.. |image34| image:: .\/media/image32.png
.. |image35| image:: .\/media/image33.png
.. |image36| image:: .\/media/image34.png
.. |image37| image:: .\/media/image35.png
.. |image38| image:: .\/media/image36.png
.. |image39| image:: .\/media/image37.png
.. |image40| image:: .\/media/image38.png
.. |image41| image:: .\/media/image39.png
.. |image42| image:: .\/media/image40.png
.. |image43| image:: .\/media/image41.png
.. |image44| image:: .\/media/image42.png
.. |image45| image:: .\/media/image43.png
.. |image46| image:: .\/media/image44.png
.. |image47| image:: .\/media/image45.png
.. |image48| image:: .\/media/image18.png
.. |image49| image:: .\/media/image25.png
.. |image50| image:: .\/media/image19.png
.. |image51| image:: .\/media/image46.png
.. |image52| image:: .\/media/image12.png
.. |image53| image:: .\/media/image13.png
.. |image54| image:: .\/media/image47.png
.. |image55| image:: .\/media/image48.png
.. |image56| image:: .\/media/image49.png
.. |image57| image:: .\/media/image50.png
.. |image58| image:: .\/media/image51.png
.. |image59| image:: .\/media/image6.png
.. |image60| image:: .\/media/image5.png
.. |image61| image:: .\/media/image7.png
.. |image62| image:: .\/media/image9.png
.. |image63| image:: .\/media/image10.png
.. |image64| image:: .\/media/image52.png
.. |image65| image:: .\/media/image11.png
.. |image66| image:: .\/media/image53.jpeg
.. |image67| image:: .\/media/image54.jpeg
.. |image68| image:: .\/media/image55.png
.. |image69| image:: .\/media/image57.png
.. |image70| image:: .\/media/image58.png
.. |image71| image:: .\/media/image59.png
.. |image72| image:: .\/media/image38.png
.. |image73| image:: .\/media/image39.png
.. |image74| image:: .\/media/image40.png
.. |image75| image:: .\/media/image2.png
.. |image76| image:: .\/media/image60.png
.. |image77| image:: .\/media/image61.png
.. |image78| image:: .\/media/image6.png
.. |image79| image:: .\/media/image5.png
.. |image80| image:: .\/media/image7.png
.. |image81| image:: .\/media/image16.jpeg
.. |image82| image:: .\/media/image9.png
.. |image83| image:: .\/media/image10.png
.. |image84| image:: .\/media/image52.png
.. |image85| image:: .\/media/image11.png
.. |image86| image:: .\/media/image12.png
.. |image87| image:: .\/media/image14.jpeg
.. |image88| image:: .\/media/image14.jpeg
.. |image89| image:: .\/media/image17.png
.. |image90| image:: .\/media/image22.png
.. |image91| image:: .\/media/image62.png
.. |image92| image:: .\/media/image63.png
.. |image93| image:: .\/media/image64.png
.. |image94| image:: .\/media/image13.png
.. |image95| image:: .\/media/image65.png
.. |image96| image:: .\/media/image44.png
.. |image97| image:: .\/media/image47.png
.. |image98| image:: .\/media/image44.png
.. |image99| image:: .\/media/image66.png
.. |image100| image:: .\/media/image67.png
.. |image101| image:: .\/media/image68.png
.. |image102| image:: .\/media/image49.png
.. |image103| image:: .\/media/image50.png
.. |image104| image:: .\/media/image48.png
.. |image105| image:: .\/media/image42.png
.. |image106| image:: .\/media/image42.png
.. |image107| image:: .\/media/image69.jpeg
.. |image108| image:: .\/media/image70.png
.. |image109| image:: .\/media/image71.png
.. |image110| image:: .\/media/image46.png
.. |image111| image:: .\/media/image72.png
.. |image112| image:: .\/media/image14.jpeg
.. |image113| image:: .\/media/image18.png
.. |image114| image:: .\/media/image73.png
.. |image115| image:: .\/media/image74.png
.. |image116| image:: .\/media/image45.png
.. |image117| image:: .\/media/image25.png
.. |image118| image:: .\/media/image75.png
.. |image119| image:: .\/media/image76.png
.. |image120| image:: .\/media/image77.png
.. |image121| image:: .\/media/image78.png
.. |image122| image:: .\/media/image79.png
.. |image123| image:: .\/media/image80.png
.. |image124| image:: .\/media/image46.png
.. |image125| image:: .\/media/image81.png
.. |image126| image:: .\/media/image82.png
.. |image127| image:: .\/media/image19.png
.. |image128| image:: .\/media/image83.png
.. |image129| image:: .\/media/image84.png
.. |image130| image:: .\/media/image85.png
.. |image131| image:: .\/media/image86.png
.. |image132| image:: .\/media/image46.png
.. |image133| image:: .\/media/image87.png
.. |image134| image:: .\/media/image88.png
.. |image135| image:: .\/media/image46.png
.. |image136| image:: .\/media/image89.png
.. |image137| image:: .\/media/image90.png
.. |image138| image:: .\/media/image46.png
.. |image139| image:: .\/media/image73.png
.. |image140| image:: .\/media/image91.png
.. |image141| image:: .\/media/image41.png
.. |image142| image:: .\/media/image43.png
.. |image143| image:: .\/media/image92.png
.. |image144| image:: .\/media/image93.png
.. |image145| image:: .\/media/image94.png
.. |image146| image:: .\/media/image95.png
.. |image147| image:: .\/media/image96.png
.. |image148| image:: .\/media/image98.png

