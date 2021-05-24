# Westway-Diner-Data-Model

<b>You are working at a restaurant and the owner wants to track the profit and profit margin of the menu at the item level. Build the data infrastructure required to answer the owner’s question.</b>
<ul>
  <li> You know how much the business charges for a meal and how much the individual items cost to source from the distributors, but you don’t know the cost to make the meal. </li>
  <li> Meals don’t necessarily use whole ingredients. For example, a sandwich could use half of a tomato. </li>
</ul>

The two issues that I saw up front was how to map customizations and ingredients to food items. For example, there may be customizations that are “set in stone” such as Belgium Waffles + Bacon, but we need to think about how to charge customers that go “off script”, for example Belgium Waffles + Every Fruit. My solution to both problems is to store every customization as a food item and change the way orders are documented. By storing all the customizations separate we can track the profits of the customizations as well. <br />

The downfall that I see to this is that it would be difficult to track the profit of “pairs”  of items such as Belgium + Bacon. Tracking pairs could be important; picture this:
<ul>
  <li> The profit of the Belgium waffle is high. </li>
  <li> The profit of bacon is negative. </li>
</ul>

The company is thinking of removing bacon from the menu, however what if the people who buy Belgium Waffles mainly add the bacon customization. Furthermore, the customer sentiment is that the “Belgium Waffle isn’t worth it without the bacon”. Removing bacon could potentially do more harm than good. I see two solutions to the "Bacon Profit Paradox":
<ul>
  <li> Take the profit hit because other items are making up for it. </li>
  <li> Increase the price of bacon to be <b>AT LEAST</b> 0 profit. </li>
</ul>

<i>I think these cases can generally be ignored since tracking combinations is an unsustainable venture. The restaurant will have a set of customizables and base items. The number of customization “pairs” could be ESTIMATED by: </i>

<p align='center'>
    <img align='center' width='250' src="https://render.githubusercontent.com/render/math?math=\textrm{Pairs} = \textrm{Base Items} \cdot \sum_{k=1}^{C}{C \choose k}"> 
</p>

<i>If you had 10 base items and 5 customizables, that would be 310 pairs. <b>This formula can’t be taken as fact because there are some pairs that don’t make sense in regard to the likelihood of it being ordered (Coffee + Bacon)</b></i>. 

