# hts_simulator

summary: based off of the card game 'here to slay', creating a simulator to determine most optimal choice to make dependant on current game state.

things i want to learn/implement in this project:
    -object oriented programming(oop):
        -this can be applied to:
            -cards
                monsters
                party leaders
                heros
                items
                modifiers
                cursed items
            -players
                current hand
                current played cards
                slayed monster pool
                action points

general mechanics and notes:

game loop:
-each player starts with a party leader
    -party leader can grant effect, or potential action #todo confirm this
    -party leader's trait adds to party's overall type pool, but does not count towards numerical total of party for checks against monsters
-3 monster cards are played face up
-each player draws 5 cards
-players take turns until a player reaches a win condition

win conditions:
-defeat 3 monsters
-field a party containing 6 distinct hero types (including party leader type)

player turn:
    -each player starts with 3 action points (unless effected by card)
    -actions (base):
        -draw a card - one action point
        -play a card - one action point
            -hero
            -magic
            -item/cursed item
        -attack a monster - 2 action points
        -discard entire hand, draw 5 cards - 3 action points
    -once player runs out of action points, their turn is over

playing cards:
    -hero
        -can use heros ability as soon as played
        -hero stays in party and their traits are added to player's party stats
        -hero's ability can be used once per turn after initial play turn
    magic
        -typically impacts cards on board, in hand, or drawing cards
        -probably the vaguest effects
    item/cursed item
        -items can be played on either the current player's party or other player's party
        -items typically impact the hero they are equipped to
            -can change a hero's statblock

monster
    -challenge requirements
        -players party has to be a certain size or contain heros/party leader with a specific type in order to challenge a monster
    -slay requirement
        -player needs to roll a certain value or higher in order to slay the monster successfully
    -failure consequences
        -if a player rolls a certain value or lower, they must follow the failure consequence for the monster they attacked
    -upon successful slaying of monster, player keeps monster and permanently gains their listed effect

player interactions
    -modifiers
        -players can use modifiers directly after any player role including their own to increase or decrease the final result
            -once another action is taken, roll value is locked in
        -certain modifiers can have extra effects or actions depending on game state before or after use
    -challenges
        -challenges can only be played when another player plays a hero magic or item card
        -certain challenges gain effects based on the players party
        -the challenger and player challenged both roll, the higher roll results in the action passing or failing
