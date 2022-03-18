# lab4_task5_minigame
A fun RPG kind of game built on classes
This is a simple RPG-type game. The game consists of 2 python modules.
The main one can and should be modified in order to change the plot and the location of the game. The "game" module includes classes necessary to save the info about game rooms, usable items, and characters. So, in order to build a completely new game with the same mechanic, the only thing that should be changed is this part of main, where the locations, the items and the characters are created:
```python
kitchen = game.Room("Kitchen")
kitchen.set_description("A dank and dirty room buzzing with flies.")

dining_hall = game.Room("Dining Hall")
dining_hall.set_description("A large room with ornate golden decorations on each wall.")

ballroom = game.Room("Ballroom")
ballroom.set_description("A vast room with a shiny wooden floor. Huge candlesticks guard the entrance.")

kitchen.link_room(dining_hall, "south")
dining_hall.link_room(kitchen, "north")
dining_hall.link_room(ballroom, "west")
ballroom.link_room(dining_hall, "east")

dave = game.Enemy("Dave", "A smelly zombie")
dave.set_conversation("What's up, dude! I'm hungry.")
dave.set_weakness("cheese")
dining_hall.set_character(dave)

tabitha = game.Enemy("Tabitha", "An enormous spider with countless eyes and furry legs.")
tabitha.set_conversation("Sssss....I'm so bored...")
tabitha.set_weakness("book")
ballroom.set_character(tabitha)

cheese = game.Item("cheese")
cheese.set_description("A large and smelly block of cheese")
ballroom.set_item(cheese)

book = game.Item("book")
book.set_description("A really good book entitled 'Knitting for dummies'")
dining_hall.set_item(book)
```
No additional modules are required for the program to run. 
The "game" file includes 5 classes:
Room - the room where action takes place, where the items and the characters are located;
```python
>>> room = Room('kitchen')
>>> room.name
'kitchen'
```
Item - usable item that is located in a room and can be taken and used to fight an enemy;
Character - the parent class of classes enemy and friend. Saves the info about a character that is located in a room and can be interacted with;
Friend(Character) - a character that you don't have to fight, intstead, friend can give you can item for solving a riddle or sell that item to the player.
Enemy(Character) - a character that is located in a room, that you have to defeat by fighting with a previously collected item.
