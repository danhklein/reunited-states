*************************
1) Application redraws statelines according to changable parameters
applied to Census data.

Initial parameters would be number of states maximum and minimum populations, maximum and minimum geographic areas. Parameters would be given order of operations.

2) Application then would relay information about newly created States.

3) APIs can begin with census data but retrieve info for step 2 (and later added parameters of Step 1) from other APIS

__________________________________________________

1) Census API data applied to census areas on map.
****
CITY STATE STEP
****
2) Create array (density) of population ranges of urban census areas (neighborhoods). The Census defines urbanized areas (UAs) as having a population above 50k psm. (https://www.census.gov/geo/reference/urban-rural.html)

 I.e. [5e5 psm...+2e5 psm, 1.9e5 - 1.99e5, 1.9e5-1.949, 1.85e5-1]

  2a) Take element in array (starting with highest population(index [0])), select it on map and add it to a new empty array. (i.e. state1, state 2, state 3). Array is assigned color.

  2b ). Use new loop to push all adjacent and concurrent UAs (Urban Areas) into that array.

  2c) Break when either
   (1)no more (UA) adjacent
      A) if no more UA adjacent, wait for step 3.
   (2) enclosed or hit population or geography max.
      A) If enclosed or hits population or geography max, state is done.
        i) Asks for name of State or offers one.
        ii) Describes state using census data.

  2d) Loop through density array until number of states parameter has been reached.

  ________________Minimal States_________________

  At this point there is a X number of states, but some may not have reached the geographic or population minimum.

  3A) Depending on parameter priority, order state array by either lowest population or geography.

  3b) Add adjacent tracts until reaches higher priority minimum then stop.

  3c) If state is enclosed before reaching a minimum surrounding states that had passed minimum would "break" and tracts would be absorbed into first state.

  _______________Finishing States________________

  Now finish states. All states that haven't reached max take turns absorbing untaken adjacent
  tracts. Finish when hitting limiting max or enclosed.



  Questions:

  In finishing state do want to find way to prioritize growth of smaller or lesser states in order to create more even states.

  Partly important in order to create more compact states that don't snake around each other.

  Might want to add parameter that changes density level that counts as UA.












