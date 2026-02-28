# Code Conventions
## General
- Language
  - English (always)
- Naming
    - Files/Variables/Functions/etc.: camelCase 
    - SQL Tables & Attributes: snake_case
- Write new Lines for multiple conditions and Curly Braces
    ```
    //bad
    if(moreComplexCondition() && 
        evenMoreComplexCondition()){
        //code execution
    }

    //better
    if(
        moreComplexCondition() && 
        evenMoreComplexCondition())
    {
        //code execution
    }
    ```

### Functions
Single-Responsibility-Principle.  
Functions have to follow the Single-Responsibility-Principle **(SRP)**. So functions compute little to no data on their own, and consist mostly of other function calls -> highly readable, easier to debug, to change, more flexible and generic.


#### Naming
Function names have to communicate their purpose accurately. This includes naming their parameters in a meaningful way. Read both of these versions, and imagine working in a code base with all functions named either like the first, or the second variant.
findNext(string word, int max); -> getPosOfNextOccurance(string wordToSearch, int distanceLimit);

Keep names concise and avoid redundancy.
If we have a class called Player, its functions are automatically assumed to involve the player in some way.

examples of bad -> good names:
checkIfPlayerHasAllNeededItemsToEnterDoor() -> hasRequiredItemsToEnter()
Player.movePlayerVerticallyRelativeToPlayer() -> Player.moveByLines()
Player.movePlayerVerticallyToLineInMap() -> Player.moveToLine()




## If’s and Loops
#### Avoid ifs and fors if possible
If’s, f and their conditions take time to read and get quickly become confusing. Oftentimes, if’s can be replaced by ternary expressions, methods, or function calls, and loops by built-in functions, or other means.

#### Keep Nesting minimal

Instead of 
```
if (canMove())
{
	return;
}
else
{
	//move logic
}
```
write

```
if (!canMove())
    return; 

//move logic
```

#### Minimize Negations
When writing conditions, avoid negations where possible and prefer to make the "positive" version, the true branch. This reduces the amount of "mental flips" when reading code, which is much faster and less prone to mistakes. 
 for example
```
    // bad
    if (!hasItem() && !(x <= y)) 

    // better
    if (hasItem() || x > y)
```

## Git
#### Issue Cycle
1. Create Issue
    - Add description
    - Approvers
2. Create Branch
3. Repeat until approved:
    - Write Code ->
    - Push ->
    - Get Reviewed ->
4. Merge

#### Commits
Commits should be made very frequently, at least after an easily defined part of code has been added/changed.    Commit messages should summarize the changes.

Merge Commit messages must describe everything that is added. When reading through the merge messages, one must get informed all the important changes that have been made to the codebase.
