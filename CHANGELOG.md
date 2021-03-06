## 0.2.10 - 28/02/21
- Ran 'run_experiments.py' for all experiment sets to produce contents in 'outputs' dir, 
excluding 'max_num_lookaheads' = 0 due to simulation not working for that setting
- Ran 'analyse_csv.py' to produce 'outputs_analysis.csv'
- Minor bug fixes to 'analyse_csv.py' as they came up

## 0.2.9 - 25/02/21
- Modified 'analyse_csv.py' to output the results of the analyses of experiments to .csv, 
along with the settings of the specific experiment set / experiment / repetitions and 
which settings in config.txt were modified by 'analyse_csv.py'

## 0.2.8 - 23/02/21
- Modified 'run_experiments.py' to work with arguments, including starting/ending indeces 
within the experiment settings file and enabled the running of multiple repetitions of the same experiment
- Modified 'analyse_csv.py' to work with the doubly-nested files produced by the changes 
made to 'run_experiments.py' and average the analysis results over multiple repetitions

## 0.2.7 - 22/02/21
- Added experiment sets and the simulation variations required to 'experiment_settings.json'
- Modified 'run_experiment.py' to utilise these settings to run experiment sets and experiments

## 0.2.6 - 18/02/21
- Improved 'ReplicationAgent' to cause replicated agents to have mutated attributes based 
around normally generated values relative to the replicator agent's values

## 0.2.5 - 16/02/21
- Moved the 'time_delay' from setting via Simulation::run_simulation() to the config file
- Added 'output_dir' option to configuration to be able to set the directory and subdirectory 
of the output .csv (+ modified simulation accordingly)
- Added the 'disable_cout' option to configuration to be able to disable console output 
(e.g. if running 'run_experiments.py')
- Added 'run_experiments.py' script to coordinate the running of simulations in batch and 
utilising multiple settings of configurations

## 0.2.4 - 15/02/21
- Added to 'ReplicationAgent' the ability to replicate upon reaching a specific energy
- Modified simulation and other files to account for new agents being created at runtime
- Added a minimum energy threshold to replication

## 0.2.3 - 11/02/21
- Added setter methods for x/y pos for use by ReplicationAgent during lookahead
- Improved 'ReplicationAgent' 'seek_energy()' with lookahead behaviour (i.e. to seek energies that require more than 1 move to reach)

## 0.2.2 - 09/02/21
- Added filtering of out-of-bounds search positions for ReplicationAgent
- Changed looping mechanism in 'seek_energy()' to take agent's speed into account

## 0.2.1 - 08/02/21
- Standaridation of using 'name' attribute over 'message' attribute for multiple classes
- Basic implementation of ReplicationAgent class (w/ .cpp and .h files)
- Modifications of other files to account for use of this new class

## 0.2.0 - 06/02/21
- Minor console output cleanup
- Changed simulation to use commas in .csv output instead of tabs
- Wrote Python script to analyse .csv output files + produces metrics (e.g. avg energies consumed per move)

## 0.1.16 - 04/02/21
- Move settings of simulation to config file + change simulation to use that instead of passed-in arguments

## 0.1.15 - 03/02/21
- Modified environment to initialse all predators and agents together at the same time (rather than doing so individually) 
so they are all aware of each other's existence from the beginning
- Modified 'BasicEnvironment::update()' to reflect what to do when a predator catches an agent and modified simulation to 
get rid of any dead agents on the board
- Implemented Predator as separate class not inheriting from BasicAgent

## 0.1.14 - 02/02/21
- Further work on Predator class 'seek_agent()' behaviour (inheriting much from BasicAgent but still not updating own model of 
environment correctly; should probably revert to NOT being inherited from BasicAgent; WIP)

## 0.1.13 - 01/02/21
- Basic implementation of Predator class (w/ .cpp and .h files)
- Modifications of main and simulation to recognise this new class
- Organised 'To-do.txt'

## 0.1.12 - 27/01/21
- Fixed bug w/ BasicAgent's 'check_path()', which would result in causing the agent to leap over an obstacle when approaching 
it in a negative direction
- Further improvements to AdvancedAgent's 'seek_energy()' to introduce element of random movement if stuck in a loop

## 0.1.11 - 26/01/21
- Improvements to AdvancedAgent's 'seek_energy()' function to (seemingly) no longer 'leap' over obstacles, but now gets stuck very 
easily (need to implement either random behaviour in this case to break out, or implement lookahead; WIP)

## 0.1.10 - 25/01/21
- Separated 'seek_energy()' of BasicAgent into several subroutines, which should make constructing AdvancedAgent's 
redefined 'seek_energy()' easier to implement
- Implemented behaviour in AdvancedAgent to move around obstacles during 'seek_energy()' rather than 'leaping' over them (WIP though, 
as can get stuck in a loop)

## 0.1.9 - 23/01/21
- Improved 'tasks.json' to include all .cpp files automatically, and made 'BasicAgent::state_position()' private (as already used privately)
- Setup 'AdvancedAgent' as inheriting from 'BasicAgent', in separate .cpp/.h and using necessary polymorphism alongside own 
implementation of 'seek_energy()' (implementation of full 'seek_energy()' still WIP)

## 0.1.8 - 22/01/21
- Moved header files to separate 'include' subdirectory + modify source files to utilise these, along with change in settings
- Reorganised 'Simulation.cpp'/'Simulation.h' as a single class w/ functions now as methods, and split 'run_simulation()' into two methods
- Modified .csv's to being output to separate 'outputs' directory + w/ suffixes on names based on current datetime

## 0.1.7 - 21/01/21
- Moved running of simulation to separate .cpp/.h file
- Implemented 'timed' simulation, so that window updates with each time step (e.g. once per second)
- Fix for issue with agent picking up energy on negative x/y movement but not detecting until a positive x/y movement
- Fix for issue with instantion of obstacles/energies on top of each other, resulting in fewer obstacles/energies than desired
- Added generation of .csv from simulation

## 0.1.6 - 20/01/21
- Added 'seek_energy()' function to BasicAgent

## 0.1.5 - 19/01/21
- Added 'move_random()' method to BasicAgent, which utilises existing 'move()' method with randomised arguments
- Added 'run_simulation()' to 'main.cpp' to initiate and manage a simulation
- Minor bug fixes

## 0.1.4 - 18/01/21
- Added behaviour to BasicAgent to stop at obstacle or consume energy while moving
- Added 'name' attribute for BasicAgent in place of it's 'message'
- Implemented agent move boundary checking in both positive and negative directions, and as separate 'check_bounds()' function
- Added 'update()' method to BasicEnvironment to update its copy of the board based on agents' movements and/or consumption of energies

## 0.1.3 - 17/01/21
- Implemented pointer to BasicAgent within BasicEnvironment to enable sharing of information
- Split BasicAgent and BasicEnvironment from 'basic_simulation.cpp' w/ associated header + cpp files, and renamed 'basic_simulation.cpp' to 'main.cpp'

## 0.1.2 - 16/01/21
- Added initialisation of environment tiles, along with addition of energy sources and obstacles
- Added visualisation function of environment tiles
- Added ability to add agents to environment
- Ensured agents stay within bounds when moving
- Convert BasicAgent 'move_x()' and 'move_y()' into single 'move()' method
- (WIP) Enable BasicAgent move behaviour to reflect in environment and in own state
- Moved stuff to 'src' subdirectory

## 0.1.1 - 15/01/21
- Added to-do list
- Changed repo name and local project name from 'CPP-Project' to 'Agent_Survival_Simulation'
- Added BasicAgent and BasicEnvironment classes to 'basic_simulation.cpp'
- Added Obstacle and Energy structs to 'basic_simulation.cpp'

### 0.1.0 - 13/01/21
- Initial commit
- Added project description