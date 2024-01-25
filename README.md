Overview-

Congratulations, you’ve just won the lottery and decided to use the money to start a Rutgers merch store! You have some warehouse space to store your inventory, but you are having trouble keeping track of what items you currently have in stock. Your warehouse can store up to 50 different product types, and being a new store, you will be frequently adding new products. You need a structure that can efficiently look up products and delete underperforming ones to make space for new items.

Design-

You settle on a Hash Table like structure, where each entry of the table stores a priority queue. Due to your limited space, you are unable to simply rehash to get more space. However, you can use your priority queue structure to delete less popular items and keep the space constant.
Your warehouse is split into 10 sectors, each of which can hold 5 product types.
The last digit of the product ID determines which sector it should go into. Then when we search for it, we can immediately narrow down the search to at most 5 items rather than searching through the entire warehouse.
You settle on a simple metric for how well an item is doing: Popularity = Initial Demand + Total Amount Purchased + Date of Last Purchase. The initial demand is obtained from a survey prior to product release, and the date of last purchase is simply the number of days since the store opening that the item was last purchased.
You want to be able to delete the least popular item in a sector efficiently, so you decide to make each sector a min heap ranked by popularity.
Even though each sector is a min heap, it can still function as a normal list, which you can search through sequentially.

Overview of Files-

Warehouse.java- 

This class implements a warehouse on a Hash Table like structure, where each entry of the table stores a priority queue. Due to limited space, I am unable to simply rehash to get more space, so I use my priority queue structure to delete less popular items and keep the space constant.

Method files-

All the various methods created for this assignment, including AddProduct, PurchaseProduct, Restock, ect. Each class is expected to take 2 command line arguments, an input file and an output file.

Input files-

Each subtask has a corresponding .in file to test the method.

Product.java-

Contains the product ID, name, stock, date of last purchase, demand, and overall popularity. The demand is simply the sum of the initial demand for the product and the number purchased.
Getters and setters are provided, as well as special methods to update the stock and demand by some positive or negative amount.
Popularity is automatically calculated and updated as the sum of the last purchase day and current demand.

Sector.java-

Contains an array of Products which forms a valid min heap based on popularities, as well as the current size of the sector (defined as the number of Products in it).  Contains  methods to add a Product to the end of the sector, set some index, delete the last Product, get the Product at some index and get the current size.
