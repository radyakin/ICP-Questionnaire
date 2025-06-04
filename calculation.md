### Calculated results

For every observation of price the following are calculated:

- `quantityNormalized_1` - observed quantity converted from observed units to reference units. For example, if the weight of the observed item was exactly *2lbs* and the reference unit is *kilogram*, then the normalized quantity is *0.907185kg*.

- `priceNormalized_1` - this is the cost of the reference quantity in observed prices. (this value is expressed in currency per reference UOM).

- `priceRatio_1` - this is the ratio of the normalized price to reference price. (this value is unitless)

The values above are calculated and immediately used to validate interviewer's input:

- `quantityNormalized_1` is used to verify that the observed quantity is within the specified [min;max] range for this item. If not - an error is displayed to the interviewer.

- `priceRatio_1` is used to verify that the price of the item is within the tolerance range around the reference price. If not - a warning is displayed to the interviewer.

For every item the number of recorded prices is calculated and displayed along with the number of requested price observations for that item:

![image](https://github.com/user-attachments/assets/2283526d-ab16-44d8-ab4c-3dc1a387c825)

In addition the program calculates the following for the *supervisors*:

- total number of shops, from which the items were collected (not displayed, but used in calculations of the shares).
- share of shops (in percent) by type (9 types of shops).
- total number of items, for which the prices are reported and shop type is known (not displayed, but used in calculations of the shares).
- share of items (in percent) by type of shops (9 type of shops).

```
Department stores and specialist superstores..........................1
Supermarkets and hypermarkets.........................................2
Cash and carry outlets................................................3
Mini-markets, service station shops, neighbourhood shops and kiosks...4
Specialised shops.....................................................5
Markets...............................................................6
Private service enterprises...........................................7
Public or semi-public service enterprises.............................8
Other kinds of outlets................................................9
```

If the representativeness of items by shop type is not a concern, then calculation 
of these statistics can be removed from the "*Shops*" section to reduce the number 
of calculations:

- question `sv_review_shop_stats`;
- question `sv_review_item_stats`;
- sub-section "*Shop statistics*";
- sub-section "*Item statistics*".

### Distribution of shops by type
![image](https://github.com/user-attachments/assets/e42c8ece-9ab1-4a99-bed3-4a265378c520)

### Distribution of items by shop type
![image](https://github.com/user-attachments/assets/b237fb77-55ed-4e4b-a342-3478d34bc86a)



