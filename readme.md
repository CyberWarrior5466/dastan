### Table of contents
- [Questions](#questions)
- [UML diagram](#uml-diagram)


## Questions
Taken from the [dastan wiki](https://en.wikibooks.org/wiki/A-level_Computing/AQA/Paper_1/Skeleton_program/2023)


1. At the beginning of the game allow each player to enter their own name instead of `Player One` or `Player Two`

   <details>
   <summary>View Solution</summary>
 
   ```python
   # note lines ending in a `##` have been changed
   class Dastan:
      def __init__(self, R, C, NoOfPieces):
         self._Board = []
         self._Players = []
         self._MoveOptionOffer = []
         self._Players.append(Player(input("Player One enter name: "), +1))  ##
         self._Players.append(Player(input("Player Two enter name: "), -1))  ##
         ...
   ```
   </details>

2. Add a new move called `TibbleCross`. This move allows a piece to move up two spaces diagonally.

   ```
   X . . . X
   . . . . .
   . . * . .
   . . . . .
   X . . . X
   ```
   
   -  This move should appear first in the queue
 
   -  To test this move the piece from the co-ordinate "22" to "44" 
   
   <details>
   <summary>View Solution</summary>
 
   ```python
   # note lines ending in a `##` have been changed
   
   def __CreateMoveOptionOffer(self):
      self._MoveOptionOffer.append("tibblecross")  ##
      self._MoveOptionOffer.append("jazair")
      ...
   
   def __CreateTibbleCrossMoveOption(self, Direction):
      NewMoveOption = MoveOption("tibblecorss")       ##
      NewMove = Move(2 * Direction, 2 * Direction)    ##
      NewMoveOption.AddToPossibleMoves(NewMove)       ##
      NewMove = Move(2 * Direction, -2 * Direction)   ##
      NewMoveOption.AddToPossibleMoves(NewMove)       ##
      NewMove = Move(-2 * Direction, 2 * Direction)   ##
      NewMoveOption.AddToPossibleMoves(NewMove)       ##
      NewMove = Move(-2 * Direction, -2 * Direction)  ##
      NewMoveOption.AddToPossibleMoves(NewMove)       ##
      return NewMoveOption                            ##
   
   def __CreateMoveOption(self, Name, Direction):
      if Name == "tibblecross":                                ##
         return self.__CreateTibbleCrossMoveOption(Direction)  ##
      elif Name == "chowkidar":                                ##
         return self.__CreateChowkidarMoveOption(Direction)
      elif Name == "ryott":
         return self.__CreateRyottMoveOption(Direction)
      elif Name == "faujdar":
         return self.__CreateFaujdarMoveOption(Direction)
      elif Name == "jazair":
         return self.__CreateJazairMoveOption(Direction)
      else:
         return self.__CreateCuirassierMoveOption(Direction)
   
   def __CreateMoveOptions(self):
      self._Players[0].AddToMoveOptionQueue(self.__CreateMoveOption("tibblecross", 1))   ##
      self._Players[0].AddToMoveOptionQueue(self.__CreateMoveOption("ryott", 1))
      self._Players[0].AddToMoveOptionQueue(self.__CreateMoveOption("chowkidar", 1))
      self._Players[0].AddToMoveOptionQueue(self.__CreateMoveOption("cuirassier", 1))
      self._Players[0].AddToMoveOptionQueue(self.__CreateMoveOption("faujdar", 1))
      self._Players[0].AddToMoveOptionQueue(self.__CreateMoveOption("jazair", 1))
      self._Players[1].AddToMoveOptionQueue(self.__CreateMoveOption("tibblecross", -1))   ##
      self._Players[1].AddToMoveOptionQueue(self.__CreateMoveOption("ryott", -1))
      self._Players[1].AddToMoveOptionQueue(self.__CreateMoveOption("chowkidar", -1))
      self._Players[1].AddToMoveOptionQueue(self.__CreateMoveOption("jazair", -1))
      self._Players[1].AddToMoveOptionQueue(self.__CreateMoveOption("faujdar", -1))
      self._Players[1].AddToMoveOptionQueue(self.__CreateMoveOption("cuirassier", -1))
   ```

   </details>

## UML diagram
Taken from [here](https://www.computingatschool.org.uk/resource-library/2022/september/aqa-skeleton-code-2023-dastan-uml)
![](dastan%20UML.drawio.png)

   
