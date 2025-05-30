# Animart

> 857 Word excluding references and code.

## Introduction
Animart is a single player mobile game. As a Shop Owner, players scan store items whilst haggling with customers and then using this money to improve states (Charisma, Shop Time etc). It took a team of four developers six weeks to get the game to a working prototype.

## Target Audience 
Children 12+ as the game has  features which would potentially be diffcult for younger children to grasp (eg keeping money back to pay rent). 

## Inspiration 
Roguelike genre Balatro, a card game in which you have to gain a certain amount of points using poker hands, which are upgradable over time.

## Unity Programming
This game was made using the 3D instance of Unity which allowed us to make our game in 2D or 3D. Our game uses a 2.5D aspect allowing you to see the table and the NPCs at the same time but also allowing us to hide certain assets behind the table making the instantiating of assets smoother.

Most of the scripts run behind the scenes collecting data which will be displayed at the end of the day. These pieces of data would then be displayed on the desk via pieces of paper.

### Score Paper
I created a large cube to hold which acts as the desk to hold the pages of scores.

![image](Media/Desk.png)

After this I created three planes which act as sheets of paper to hold the scores with a RigidBody attached to allow the paper to be lifted around the scene.

The page then has a child connected to it via TMP Text where I am able to add the text for the score after the gameplay is completed. These automatically update by reading the variable of Jack and Solar's scripts allowing me to take their values and displaying them in a way easy enough for younger players to see. 

![image](Media/Paper_stats.png)
![image](Media/Income_stat.png)
![image](Media/Rep_stat.png)

### Text Mesh Pro
The first script I created was the reputation script which would give you a value from F to A as to how high your reputation is and if it increases above 100 it will become S rank and stay there. For the prototyping of the script I used a variable called Rep as a place holder for when they would be added to main scene allowing me to access the characters stats and place them onto the sheet.

https://github.com/user-attachments/assets/3f980f8b-2912-4b6d-b723-d7a9c9e8bf10

#### Reputation Paper
The serialize field is where I connect The text asset to this script allowing this script to then show onto the paper. I used if and else if statements, allowing me to make sure each value was consistent throughout the game.

```csharp
public float Rep = 1;
[SerializeField] TMP_Text Reputation;
void Update()
{
  if (1 >= Rep)
{
  Reputation.text = "Reputation F ";
}
else if (1 <= Rep && Rep <= 15)
{
  Reputation.text = " Reputation F ";
}
else if (16 <= Rep && Rep <= 30)
{
  Reputation.text = " Reputation E ";
}
else if (31 <= Rep && Rep <= 45)
{
  Reputation.text = " Reputation D ";
}
else if (46 <= Rep && Rep <= 60)
{
  Reputation.text = " Reputation C ";
}
else if (61 <= Rep && Rep <= 75)
{
  Reputation.text = " Reputation B ";
}
else if (76 <= Rep && Rep <= 90)
{
  Reputation.text = " Reputation A ";
}
else
{
  Reputation.text = "Reputation S ";
}
```

This version of the code avoids the repeated range checks that would run every if statement and is easier to change and scale in the future.

```csharp
void Update()
{
    Reputation.text = $"Reputation {GetReputationGrade(Rep)}";
}

private string GetReputationGrade(float rep)
{
    if (rep <= 15) return "F";
    if (rep <= 30) return "E";
    if (rep <= 45) return "D";
    if (rep <= 60) return "C";
    if (rep <= 75) return "B";
    if (rep <= 90) return "A";
    return "S";
}

```

#### Money Paper
To create the money script I followed the same setup as the reputation script with a variable called money and the serial field to connect the TMP text to the script, this then takes the Shops final income so that the player can see how much money they have to spend at the end of the day. This allows the player to then purchase the upgrades that are available in the store for them whilst also allowing them to keep an eye on having enough money to succeed at the end of the in game week. To show the value on the paper I used a string Interpolation which allows the compiler to know there's an expression which needs evaluating. I used this method instead of "Income.text = money.ToString("Income: " + money)" as this then allows a value of 110 for example rather than 110110 as an output.

```csharp
public float money = 0;
[SerializeField] TMP_Text Income;

void Update()
{
  Income.text = $"Income: {money}";
}
```

#### Opening Hour Paper
The final piece of paper I had made was for opening and closing time, this piece of paper would be an upgrade that could be brought allowing player to have more time to serve more customers. This would be directly linked to the timer and is connected by being in the script. To create this script I had to do the same TMP text on to the paper and then create a timer which I did using a TMP canvas and shows the timer always at the centre top. To display text on to these areas I used a serialize field to attach both areas of text as well as a variable call remaining time which was set to 300.

```csharp
[SerializeField] TMP_Text openTime;
[SerializeField] TextMeshProUGUI timerText;
float remainingTime = 300;
```

After setting these references I then added the variable Timer which will run every frame and constantly update the Timer function.

```csharp
// Update is called once per frame
void Update()
{
  Timer();
}
```

Finally I made the timer which which will constantly check if the time is bigger than 0 and if it is it will proceed to take away time in seconds. 


```csharp
void Timer()
{
  if (remainingTime > 0)
  {
    remainingTime -= Time.deltaTime;
  }
  else if (remainingTime < 0)
  {
    remainingTime = 0;
    Debug.Log ("Game Over");
  }
```

The last part of the timer code was the set up for the timer in the centre of the screen.

```csharp        
  int Minutes = Mathf.FloorToInt(remainingTime / 60);
  int Seconds = Mathf.FloorToInt(remainingTime % 60);
  timerText.text = string.Format("{0:00}:{1:00}", Minutes, Seconds);
}
```

https://github.com/user-attachments/assets/23dbc872-1d18-405e-a1e8-d87d8a91181a

### Conclusion
Whilst there are aspects of the game that still need to be built, we have nonetheless created a working prototype and have a shared understanding of what would need to be done to complete it.  In particular, I now recognise that using the Unity manual more closely instead of using simple ways of writing this code would have been beneficial.

# Reference
- [Unity manual](https://docs.unity3d.com/2022.3/Documentation/Manual/UnityManual.html) (2022)
- [Make a TIMER & COUNTDOWN in 5 Mins | Unity Tutorial for Beginners by Rehope Games](https://www.youtube.com/watch?v=POq1i8FyRyQ&t=185s)-Youtube (2024)
- [Balatro](https://www.playbalatro.com)(2024)


