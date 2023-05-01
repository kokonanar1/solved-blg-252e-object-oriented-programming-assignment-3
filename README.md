Download Link: https://assignmentchef.com/product/solved-blg-252e-object-oriented-programming-assignment-3
<br>



<h1>Introduction</h1>

For this assignment, you are expected to implement classes for a text-based strategy game called <strong>“The Warmonger: A New Dimension”</strong>.

In this game, players play as a war merchant trying to keep a war in balance to profit themselves the most. During the game, players can sell weapons and armors to different factions by considering their stats and attack behavior. Number of weapons and armors that players can sell is limited in every turn; therefore, they need to consider how much equipment they need to sell without disturbing the balance and losing max profit.

In each turn, players can

<ul>

 <li>see the information of faction(s);</li>

 <li>sell weapons and armors to all the factions at war;</li>

 <li>end the turn(day) after selling as much as equipment they want within the limit; end the current game they are playing;</li>

 <li>quit the game.</li>

</ul>

To better understand the game, you can watc<a href="https://www.youtube.com/watch?v=icjZpcCg8OA">h </a><a href="https://www.youtube.com/watch?v=icjZpcCg8OA"><strong>the gameplay video</strong></a><a href="https://www.youtube.com/watch?v=icjZpcCg8OA">.</a>

For any issues regarding the assignment, please ask in <strong>Ninova message board</strong> or contact <strong>Uğur Önal (<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="6d02030c01180a2d0419184308091843191f">[email protected]</a>)</strong>.

<h2>Implementation Notes</h2>

The implementation details below are included in the grading:

<ol>

 <li><strong>cpp</strong> file is provided to you in the homework files. Do not change it since we will evaluate your homework with it.</li>

 <li>Please follow a consistent coding style (indentation, variable names, etc.) with comments.</li>

 <li>You are not allowed use STL containers.</li>

 <li>You should implement any getter and setter methods when they are needed. You <strong>should use the method names</strong> used in <strong>cpp</strong>.</li>

 <li>Allocate memories dynamically for arrays and implement necessary destructors where the allocated memory parts are freed. Make sure that there is no memory leak in your code.</li>

 <li>Make use of constants and call by reference appropriately</li>

 <li>Make sure that you used proper access modifiers for attributes in terms of <strong>public</strong>, <strong>protected</strong> and <strong>private</strong>.</li>

 <li>Print out your messages to the terminal. Do not create a .txt file to print into.</li>

 <li>Since your code will be tested automatically, make sure that your outputs match with sample scenario for given inputs.</li>

</ol>







<h1>1       Implementation Details</h1>

You are expected to implement 5 classes: <strong>Faction, Orcs, Dwarves, Elves </strong>and<strong> Merchant</strong>.

<h2>1.1       Faction</h2>

<strong><u>Private Attributes:</u></strong>

Faction class <strong><em>has</em></strong>

<ul>

 <li>a <strong>name </strong>(e.g., “Default”),</li>

 <li>a Faction pointer representing <strong>first enemy</strong>,</li>

 <li>a Faction pointer representing <strong>second enemy</strong>,</li>

 <li>a <strong>number of units </strong>(e.g., 50),</li>

 <li>an <strong>attack point </strong>(e.g., 30),</li>

 <li>a <strong>health point </strong>(e.g., 150),</li>

 <li>a <strong>unit regeneration number </strong>(e.g., 10),</li>

 <li>a <strong>total health </strong>which is the multiplication of the number of units and health point (e.g. 8000),</li>

 <li>a flag controlling if the faction <strong>is alive</strong> (e.g., true).</li>

</ul>

<strong><u>Methods:</u></strong>

<ol>

 <li><strong>Constructor: </strong>the constructor should <strong><em>optionally</em></strong> take the name, number of units, attack point, health point, unit regeneration number attributes. It sets the total health value and makes the alive status true.</li>

 <li><strong>AssgnEnemies: </strong>a method to assign enemies for the faction. Enemy factions are assigned to the faction to manipulate during the game.</li>

 <li><strong>PerformAttack</strong>: a pure virtual method to perform attack by the faction’s attack behavior.</li>

 <li><strong>ReceiveAttack</strong>: a pure virtual method to receive attack from an enemy faction and act on it by the Faction’s damage behavior.</li>

 <li><strong>PurchaseWeapons</strong>: a pure virtual method to receive weapon from the merchant and return the profit.</li>

 <li><strong>PurchaseArmors</strong> a pure virtual method to receive armor from the merchant and return the profit.</li>

 <li><strong>Print: </strong>a virtual method to print Faction information in the format below.</li>

</ol>

Faction Name:         &lt;name&gt;

Status:               &lt;“Alive” or “Defeated”&gt;

Number of Units:      &lt;numOfUnits&gt;

Attack Point:         &lt;attackPoint&gt;

Health Point:         &lt;healthPoint&gt; Unit Regen Number:    &lt;unitRegen&gt;

Total Faction Health: &lt;totalHealth&gt;

<ol start="8">

 <li><strong>EndTurn: </strong>a method to set the Faction’s information at the end of the turn. This method updates the number of units, total health and alive status of the faction.

  <ul>

   <li>If the number of units is less than 0 at the end of the turn, method should set it to 0.</li>

   <li>If the number of units is 0, it should set alive status to false.</li>

  </ul></li>

</ol>

<strong>Warning: </strong>If you need any other methods for Faction class, you are expected to implement them as an inline function.

<h2>1.2       Orcs</h2>

<strong><u>Private Attributes:</u></strong>

Orcs class <strong><em>is</em></strong> a Faction class. It uses all of the private attributes of the Faction class and does not have any other private attributes.




<strong><u>Methods:</u></strong>

<ol>

 <li><strong>Constructor: </strong>the constructor behaves exactly like Faction class constructor.</li>

 <li><strong>PerformAttack: </strong>a method to perform attack to enemy factions.

  <ul>

   <li>If there is only one enemy faction left alive, attacks the enemy faction with all of the units with attack point.</li>

   <li>If both enemy factions are alive, attacks Elves with 70% of its units with attack point and attacks Dwarves with rest of the units with attack point.</li>

  </ul></li>

 <li><strong>ReceiveAttack: </strong>method to receive attack from an enemy faction. Reduces number of units by total damage received divided by health point.

  <ul>

   <li>If attacking faction is Elves, incoming attack point is reduced to 75% of its original value.</li>

   <li>If attacking faction is Dwarves, incoming attack point is reduced to 80% of its original value.</li>

  </ul></li>

 <li><strong>PurchaseWeapons: </strong>method to purchase weapons from the merchant. Increases attack point by double of weapon points bought and returns 20 gold for each weapon point bought.</li>

 <li><strong>PurchaseArmors: </strong>method to purchase armors from the merchant. Increases health point by triple of armor points bought and returns 1 gold for each armor point bought.</li>

 <li><strong>Print: </strong>method to print Faction information. Prints the battle cry of Orcs: <strong>“Stop running, you’ll only die tired!”</strong> in quotes then prints the information as same as the Faction class.</li>

</ol>

<h2>1.3       Dwarves</h2>

<strong><u>Private Attributes:</u></strong>

Dwarves class <strong><em>is</em></strong> a Faction class. It uses all the private attributes of the Faction class and does not have any other private attributes.

<strong><u>Methods:</u></strong>

<ol>

 <li><strong> Constructor: </strong>the constructor behaves exactly like Faction class constructor. <strong>2.</strong><strong> PerformAttack: </strong>a method to perform attack to enemy factions.</li>

</ol>

<ul>

 <li>If there is only one enemy faction left alive, attacks the enemy faction with all of the units with attack point.</li>

 <li>If both enemy factions are alive, attacks each enemy faction with half of its units with attack point.</li>

</ul>

<ol start="3">

 <li><strong>ReceiveAttack: </strong>method to receive attack from an enemy faction. Reduces number of units by total damage received divided by health point.</li>

 <li><strong>PurchaseWeapons: </strong>method to purchase weapons from the merchant. Increases attack point by weapon points bought and returns 10 gold for each weapon point bought.</li>

 <li><strong>PurchaseArmors: </strong>method to purchase armors from the merchant. Increases health point by double of armor points bought and returns 3 gold for each armor point bought.</li>

 <li><strong>Print: </strong>method to print Faction information. Prints the battle cry of Dwarves: <strong>“Taste the power of our axes!”</strong> in quotes then prints the information as same as the Faction class.</li>

</ol>

<h2>1.4       Elves</h2>

<strong><u>Private Attributes:</u></strong>

Elves class <strong><em>is</em></strong> a Faction class. It uses all the private attributes of the Faction class and does not have any other private attributes.

<strong><u>Methods:</u></strong>

<ol>

 <li><strong>Constructor: </strong>the constructor behaves exactly like Faction class constructor.</li>

 <li><strong>PerformAttack: </strong>a method to perform attack to enemy factions.

  <ul>

   <li>When attacking Dwarves, attack point is increased to 150%.</li>

   <li>If there is only one enemy faction left alive, attacks the enemy faction with all of the units with attack point.</li>

   <li>If both enemy factions are alive, attacks Orcs with 60% of its units with attack point and attacks Dwarves with rest of the units with attack point.</li>

  </ul></li>

 <li><strong>ReceiveAttack: </strong>method to receive attack from an enemy faction. Reduces number of units by total damage received divided by health point.

  <ul>

   <li>If attacking faction is Orcs, incoming attack point is increased to 125% of its original value.</li>

   <li>If attacking faction is Dwarves, incoming attack point is reduced to 75% of its original value.</li>

  </ul></li>

 <li><strong>PurchaseWeapons: </strong>method to purchase weapons from the merchant. Increases attack point by double of weapon points bought and returns 15 gold for each weapon point bought.</li>

 <li><strong>PurchaseArmors: </strong>method to purchase armors from the merchant. Increases health point by quadruple of armor points bought and returns 5 gold for each armor point bought.</li>

 <li><strong>Print: </strong>method to print Faction information. Prints the motto of Elves: <strong>“You cannot reach our elegance.”</strong> in quotes then prints the information as same as the Faction class.</li>

</ol>

<h2>1.5       Merchant</h2>

<strong><u>Private Attributes:</u></strong>

Merchant class <strong><em>has</em></strong>

<ul>

 <li>a Faction pointer representing <strong>first faction</strong> in the battlefield,</li>

 <li>a Faction pointer representing <strong>second faction</strong> in the battlefield,</li>

 <li>a Faction pointer representing <strong>third faction</strong> in the battlefield,</li>

 <li>a fixed <strong>starting weapon point </strong>(e.g., 10),</li>

 <li>a fixed <strong>starting armor point </strong>(e.g., 10),</li>

 <li>a <strong>revenue </strong>(e.g., 360),</li>

 <li>an <strong>weapon point </strong>left for the day (e.g., 5),</li>

 <li>an <strong>armor point </strong>left for the day (e.g., 6).</li>

</ul>

<strong><u>Methods:</u></strong>

<ol>

 <li><strong>Constructor: </strong>the constructor should <strong><em>optionally</em></strong> take the starting weapon point and starting armor point attributes. It sets the weapon point and armor point and makes the revenue 0.</li>

 <li><strong>AssgnFactions: </strong>a method to assign factions in the battlefield. Factions in the battlefield are assigned to the merchant to manipulate during the game.</li>

 <li><strong>SellWeapons</strong>: a method to sell weapons to a faction. Sells weapons to faction named with weapon points given, notifies players with <strong>“Weapons sold!”</strong> and returns true<strong>.</strong>

  <ul>

   <li>If faction tried to sell weapons is not alive, notifies players with <strong>“The faction you want to sell weapons is dead!”</strong> and returns false.</li>

   <li>If weapon points tried to sell is greater than the available, notifies players with <strong>“You try to sell more weapons than you have in possession.”</strong> and returns false.</li>

  </ul></li>

 <li><strong>SellArmors</strong>: a method to sell armors to a faction. Sells armors to faction named with armor points given, notifies players with <strong>“Armors sold!”</strong> and returns true<strong>.</strong>

  <ul>

   <li>If faction tried to sell armors is not alive, notifies players with <strong>“The faction you want to sell armors is dead!”</strong> and returns false.</li>

   <li>If armor points tried to sell is greater than the available, notifies players with <strong>“You try to sell more armors than you have in possession.”</strong> and returns false.</li>

  </ul></li>

 <li><strong>EndTurn</strong>: a method to set the Merchant’s information at the end of the turn. Sets the weapon and armor points to the starting values set in the constructor.</li>

</ol>


