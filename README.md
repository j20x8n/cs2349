java cThe University of Birmingham
School of Computer Science
Assignment 2 – Text Based Game
Deadline: 16:00, Dec 12, 2024
Version 1.0
An Assignment submitted for the UoB:
Object Oriented Programming
November 25, 2024Start of the revision history table
Revision History
Revision Date Author(s) Description
1.0 10/11/2024 PJ Initial version.
1Contents
1 Process For Assignment 2 4
2 Introduction 5
3 Mark allocations 5
3.1 Minimum expected commands . . . . . . . . . . . . . . . . . . . . . . 5
3.2 Minimum game requirements . . . . . . . . . . . . . . . . . . . . . . . 6
4 Full class hierarchy 7
5 Task 1 - org.uob.a2.gameobjects 7
6 Task 2 - org.uob.a2.commands 8
7 Task 3 - org.uob.a2.parser 8
8 Task 4 - org.uob.a2.utils 8
9 Task 5 - Game.java 9
10 Task 6 - New features 9
11 Submission Procedure 9
12 Rubric 10
13 Sample Output 11
2*Rules*
1. For each class refer to its corresponding test to verify ffeld and method naming
conventions.
2. Although there are many ways to construct an application, you are required to
adhere to the rules stipulated below (to achieve marks).
3. If variable names are not stipulated, you can use your own names for variables.
This shows that you have written the application (we will check for plagiarism).
4. For Assignment 2 you MAY import additional Java packages in your project, but
only those that are part of the standard Java library (e.g., java.util, java.io, etc.).
Using third-party libraries or packages not included with the standard JDK is
NOT permitted.
5. Do NOT change or modify ffles included in the "test", "lib" or "out" folders.
6. Do NOT modify the template code. However, you are allowed to create your own
methods or classes if they are needed.
7. You MUST complete this assignment independently – Do NOT discuss or share
your code with others, and Do NOT use ChatGPT! Any cheating behaviour will
result in a zero score for this module and will be subject to punishment by the
University.
8. It is *STRONGLY ADVISED AGAINST* utilizing any translation software (such
as Google Translate) for the translation of this document.
9. The jUnit tests included in the skeleton code are basic and only scratch the surface
in evaluating your code. Passing these tests does not guarantee a full mark.
10. Wrong ffle structure leads to a substantial penalty. Make sure you have followed
the Submission Instructions on the Assignment 2 Canvas page.
11. Make sure you have pushed the version of your code that you want marked to
gitlab.
12. Make sure you keep your video recording to the time limit. Any videos longer
that 7 minutes will be penalised and videos over 10 minutes will receive zero. DO
NOT compress your video in SIZE or TIME.
13. Late submissions are accepted only for 24 hours after the deadline and are penalised
 at 5% of the ffnal assessment mark.
3IMPORTANT READ THIS FIRST:
1 Process For Assignment 2
Make sure you follow the process as outlined below. Assignment 2 has a different
structure and a somewhat different approach to Assignment 1:
1. Clone the repo for assignment 2. (If you haven’t yet accessed gitlab.cs.bham.ac.uk
do so ASAP.)
2. Download and unzip the docs.zip JavaDoc ffle to your own device. In the root
folder open the IndexAll.html ffle. Read through all the package, class, method
and ffeld deffnitions and descriptions.
3. Complete each class in the src folder as deffned in the docs.
4. The suggested order for completing classes is:
(a) All classes in org.uob.a2.gameobjects.
(b) All classes in org.uob.a2.commands.
(c) All classes in org.uob.a2.parser.
(d) All classes in org.uob.a2.utils.
(e) The Game.java class.
5. For each class:
(a) Complete the required code (methods and attributes).
(b) Run your code using the run.sh command, ensuring it compiles without
errors.
(c) Test your code using the test.sh command. You will have errors at ffrst
but they should hopefully decrease as you progress.
(d) git add, git commit, and git push your code.
6. Keeping testing after each class is implemented until everything is working.
7. Add the required new features:
(a) Display a map.
(b) Adding a score. You can decide on the rules for how the scoring works but
you need to clearly explain it in the video and game.
(c) Combining items.
42 Introduction
In this assignment, you are tasked with updating the Zork style text based game from
Assignment 1(https://en.wikipedia.org/wiki/Zork). Please note that it is likely that you
will need to start from scratch due to the redesign of the game, but you ARE allowed to
reuse your story and and puzzles from Assignment 1.
The game is played by the user entering in various commands (e.g. "move south",
"look room", "get key", "use key on chest"), to which the game responds with text based
output (e.g. "You pick up the rusty key").
3 Mark allocations
You will receive marks based on two aspects of the game: Firstly, the results of running
the test.sh command. We will run our own version of these tests once you have
submitted. This command will test each class and method (detailed as in the provided
docs.zip and in Tasks 1 - 6). You need to implement all the classes and methods as
described in the docs as well as any required for your new features.
Secondly, you will need to submit a screen recording showing you playing the game
and discussing the code. Your screen recording needs to have the following:
• Show your face and your student card.
• Play through the game once showing all the rooms, puzzles and an example of
each of the expected commands.
• Show and briefly explain the code in your Game.java file.
• Show and briefly explain your required new features.
• Show and briefly explain anything else that you did beyond the normal scope of
the assignment. This includes any additional features you’ve added.
The screen recording must be shorter than 7 minutes. You can use a text-to-speech
app if you do not want to record your own voice.
3.1 Minimum expected commands
The following is a complete list of commands the game must be able to parse (values
in angle brackets refer to arguments given to a command, the pipe symbol refers to
different options):
• move : Move to a different location as defined by an exit’s name
(e.g., ’move north’).
• look |||: Look around the current room, at an exit, at a feature, or, at a specific item,
equipemnt or feature.
5• get : Pick up an item or equipment from the
current room (e.g., ’get key’).
• drop : Drop an item or equipment from your
inventory (e.g., ’drop key’).
• use  on|with : Use an item in your inventory
on its own, or on a feature or item (e.g., ’use lamp’ or ’use key on chest’).
• status : Check
your current status, or inventory; or get more information about a specific item or
equipment in your inventory.(e.g. ’status player’, ’status inventory’, ’status key).
Also able to display the map and your score.
• help : Display this help information or get help on a specific topic (e.g.,
’help move’ or ’help’).
• combine 代 写data、Java
代做程序编程语言 and : Combine two items into a new item or equipment.
(e.g., ’combine stick and rock’ or ’combine egg and flour’).
• quit: Exit the game.
NOTE: Some of these commands are not included in the template code and
need to be added i.e. combine, status map, status score
3.2 Minimum game requirements
The following are the minimum requirements for the game. You are welcome to add
more if you want to:
• At least ten (10) unique rooms or areas.
• At least two (2) features/chests.
• At least four (4) items.
• At least two (2) pieces of equipment.
64 Full class hierarchy
org.uob.a2
- Game
org.uob.a2.commands
- Command (abstract)
- Drop
- Get
- Help
- Look
- Move
- Quit
- Status
- Use
- CommandErrorException
- CommandType (enum)
org.uob.a2.gameobjects
- GameObject (abstract)
- Container (extends Feature)
- Equipment (implements Usable)
- Exit
- Feature
- Item
- GameState
- Player
- Room
- Map
- Usable (interface)
- UseInformation
org.uob.a2.parser
- Parser
- Token
- TokenType (enum)
- Tokeniser
org.uob.a2.utils
- GameStateFileParser
5 Task 1 - org.uob.a2.gameobjects
These classes represent all the game objects (i.e. Map, Item etc.) that will be used in
the game. The GameState class contains the current state of the game. The Container
class represents anything that can "contain" another object. This is implemented as
another hidden equipment or item in the room which is then revealed when the container
is "opened". Usable is an interface that makes GameObjects usable by enforcing access
7to a GameObjects UseInformation attribute.
6 Task 2 - org.uob.a2.commands
These classes represent all the commands that the player can execute in the game and
that are generated from the parser package. Commands work on the object name, not
the id. This package also includes an enum of all CommandTypes and an Exception.
7 Task 3 - org.uob.a2.parser
These classes convert the player’s text into into Commands that can be executed by the
game. It firstly sanitises the players input to get it into a correct format. Then it converts
it into Tokens using the tokenise method and finally it parses these Tokens use the parse
method.
8 Task 4 - org.uob.a2.utils
These classes read in a text file (as stored in the data directory) into a GameState
Object.
An example of the file is shown below and also included in the data directory:
player:pieter
map:m1
room:r1,test room,This is a test room for testing. It is bland.,false,
equipment:k0,key,An old rusty key,false,open,c1,rb1,You use the
rusty key to open the chest. Something falls to the floor...
container:c1,chest,A solid oak chest.,false
equipment:rb1,ruby,A red ruby,true,reveal,r1,e1,You active the
ruby! Hidden objects become visible!
item:d1,diamond,A test diamond,false
exit:e1,north,A door to the north,r2,true
room:r2,second room, This is the second testing room. It is even
more bland.,false
exit:e2,south,A door to the south,r1,false
The explanation of each field in the file is given below:
player:
map:
room:,,,
equipment:,,,,,,,
container:,,,
item:,,,
exit:,,,,
89 Task 5 - Game.java
This is the main java class that reads in a GameState, parses user input and executes
Commands.
10 Task 6 - New features
Displaying a map in any format you prefer using the status map command. Display
the player’s score based on any rules you choose using the status score command.
Combining two items using the combine command.
You may add methods and classes as required to get these features to work.
11 Submission Procedure
The general steps to take to complete the project are as follows:
• Set up your gitlab ssh access using the setup-git command on vlab.
• Copy your ssh key to your gitlab profile.
• Clone the template repository for assignment 2 from your gitlab.
• Work on your code, testing it regularly. Use the run.sh script to run the code as
this builds the code correctly as well.
• Use the test.sh script to test your code. This will give you an output similar to
what we will use to mark the code.
• Make sure you commit and push regularly as well.
• Make sure to add comments to your code to cleary explain what each method is
doing.
• Once you have completed the code, record a short video using MS Stream. Refer
to Section 3 for more information.
• Submit the video to canvas.
• Submit the latest commit hash to canvas.
• If there are no problems you are done with the assignment.
• If there are problems with your submission, update it accordingly and resubmit
the latest commit hash.
912 Rubric
Task Submission Type Mark
Automark Tests Passing gitlab 40
Game playthrough Canvas video submission 20
Game.java Canvas video submission 10
New features (map, score, combine) Canvas video submission 20
Additional features Canvas video submission 10
Total 100
Table 2: Mark Rubric
1013 Sample Output
Loading game...
Game loaded successfully.
This is a test room for testing. It is bland.
You see:
A test diamond
An old rusty key
A solid oak chest.
>> get key
get key
You pick up: key
>> look room
look room
This is a test room for testing. It is bland.
You see:
A test diamond
A solid oak chest.
>> use key on chest
use key on chest
You use the rusty key to open the chest. Something falls to the floor...
>> look room
look room
This is a test room for testing. It is bland.
You see:
A test diamond
A red ruby
A solid oak chest.
>> get ruby
get ruby
You pick up: ruby
>> move north
move north
No exit found in that direction.
>> use ruby
use ruby
You active the ruby! Hidden objects become visible!
>> look room
look room
This is a test room for testing. It is bland.
You see:
A test diamond
A solid oak chest.
A door to the north
>> move north
move north
Moving towards north
11>> status inventory
status inventory
You have the following equipment:
key
ruby
You have the following items:
>> status player
status player
Player Name: pieter
Inventory:
Equipment:
- An old rusty key
- A red ruby
>> help
help
Welcome to the game! Here are the available commands:
- MOVE: Move to a different location (e.g., ’move north’).
- LOOK: Look around the current room or inspect an object.
- GET: Pick up an item from the current room (e.g., ’get key’).
- DROP: Drop an item from your inventory (e.g., ’drop key’).
- USE: Use an item in your inventory (e.g., ’use key’ or ’use key on
chest’).
- STATUS: Check your current status, including inventory.(e.g. ’status
player’ or ’status inventory’).
- HELP: Display this help information or get help on a specific topic
(e.g., ’help move’).
- QUIT: Exit the game.
Explore the game world, interact with items, and enjoy the adventure!
>> quit
quit
Game over: Your current status is:
Player Name: pieter
Inventory:
Equipment:
- An old rusty key
- A red ruby
12

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
