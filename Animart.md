# Animart

## Introduction
Animart is a single player mobile game. As a Shop Owner, players scan store items to make money whilst haggling with customers and thenusing this money to improve states (Charisma, Shop Time and etc). 
Whilst upgrading after 5 in game days you would've needed to make a certian sum of money to pay rent of the shop, if you were unable to pay the rent you would lose the game and have to start from day 1 again. 

It took a team of four game developers, over six week period to get this game to a working prototype unfortunately not to the stage we would of liked however, as this game did not feature many assets or 
game machanics we were hoping to have by then deadline for this project. 

## Target Audience 
Our game was targetted towards children 12+ as this game with have some machanics which would be harder for younger children with having to keep money back to pay rent and seeing which stats you as the 
player would need to upgrade and a what times to allow you to optimise your game play. 

## Inspiration 
Our game was inspired by the Roguelike genre Balatro, which is a card game in which you have to complete certain amount of points using poker hands to collect them and upgrade throughout the game to be 
able to create larger point and win. 

## Unity Programming
I constructed my areas of the project using Unity. This game was made using the 3D instance of Unity which allowed ust o make our game in 2D or 3D as well. Our game would use a 2.5D aspect allowing you to 
see the table and the NPCs at the same time but also allowing us to hide certain assets behind the table making the instantiating of assets to seem more smooth. 

Most of the scripts would run behind the scenes collecting data which will be displayed at the end of the day. These pieces of data would then be displayed on the desk by pieces of paper each showing a 
different piece of data. 
### Score Paper
When starting our game I created a large cube to hold which would act as the desk to hold the pages of scores. 

After this I created three planes which would act as sheets of paper to hold the scores from the day people in the gameplay this would then have a RigidBody attached to allow the paper to have gravity and be 
lifted around the scene. This was then changed due to how the scene would be set. If the page had gravity it wouldnt be on the desk and leave the screen as the desk is a 2D horizontal plane.

![image]()

The page would has a child connected to it being TMP Text. This would be where I am able to add the text for the score after the gameplay is completed 
### Text Mesh Pro
### Mouse Interaction
### Feedback
### Conclusion
