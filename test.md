```diff
 class Dastan:
    def __init__(self, R, C, NoOfPieces):
       self._Board = []
       self._Players = []
       self._MoveOptionOffer = []
+      self._Players.append(Player(input("Player One enter name: "), +1))
+       self._Players.append(Player(input("Player Two enter name: "), -1))
       ...
```