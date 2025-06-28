# Lexical-Syntactic-Analyzer
Implementation of a lexical-syntactic analyzer to control an alien ship using Flex (lexical analyzer) and Bison (syntactic analyzer).

Main Features
Lexical Analysis (Flex):

Token recognition: commands (On, Off, Take-Off), movements (Turn, Move, Fly), configurations (Set-Ship, Set-Space)
Parameter extraction (coordinates, angles, states)
Handling of irrelevant spaces/comments


Syntactic Analysis (Bison):

Block structure validation START(ID): ... :END
Checking for separators between statements (;)
Mandatory ordering: configuration commands before operations


Command Conversion:

Transformation to executable format:
action(on), action(off)
turn(L/R,angle)
move(x,y,z)
init(x,y,z,state)
initspace(min_x,min_y,max_x,max_y,max_z)


Validation Semantics:

Invalid states (e.g.: connecting a spacecraft that is already connected)
Movements outside the spatial limits
Invalid turning angles (≥360°)
Flight attempts without prior Take-Off
Landings at height ≠ 0


Output generation:

Grouping of consecutive movements
Ordering: init → initspace → commands
Output formatted in output.txt (1 line/block)
