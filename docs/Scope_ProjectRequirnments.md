# Programming Project 4
## Monopoly Simulation Scope Document

**Project:** Programming Project 4 - Monopoly Simulation  
---

# Project Goal

The purpose of this project is to build a Monopoly movement simulator capable of generating landing probabilities for all 40 spaces on the Monopoly board.

The simulator will model player movement, Chance cards, Community Chest cards, jail rules, and dice rolls. The collected data will be used to analyze which spaces are landed on most frequently and how different jail-exit strategies affect long-term probabilities.

---

# Research Questions

This project aims to answer the following questions:

1. Which Monopoly spaces are landed on most frequently?
2. Do landing percentages stabilize as the number of turns increases?
3. Does the player's jail strategy affect landing probabilities?
4. Which board spaces are most impacted by jail strategy selection?

---

# In Scope

The following features WILL be implemented.

## Monopoly Board

- Standard 40-space Monopoly board
- Correct board order
- Space names and space types stored in data structures

Examples:

- GO
- Properties
- Railroads
- Utilities
- Chance
- Community Chest
- Jail
- Go To Jail
- Tax spaces

---

## Dice Rolling

- Two six-sided dice
- Random roll generation
- Doubles detection

---

## Movement Rules

- Move player forward by total dice value
- Wrap around board after passing GO
- Track board position

---

## Doubles Rule

- Track consecutive doubles
- Three consecutive doubles in the same turn sends player directly to Jail

---

## Jail Mechanics

### Strategy A

- Use Get Out of Jail Free card immediately if available
- Otherwise pay $50 immediately on next turn and leave Jail

### Strategy B

- Use Get Out of Jail Free card immediately if available
- Attempt to roll doubles for up to three turns
- If unsuccessful, leave Jail on fourth turn

---

## Chance Cards

Implement all movement-related Chance cards:

Examples:

- Advance to GO
- Go to Jail
- Advance to Illinois Avenue
- Advance to St. Charles Place
- Advance to Reading Railroad
- Advance token to nearest Utility
- Advance token to nearest Railroad
- Go back 3 spaces

Chance deck requirements:

- Shuffle at the beginning
- Draw cards in order
- Discard after use
- Reshuffle when deck becomes empty

---

## Community Chest Cards

Implement all movement-related Community Chest cards:

Examples:

- Advance to GO
- Go to Jail
- Get Out of Jail Free

Community Chest deck requirements:

- Shuffle at beginning
- Draw cards in order
- Discard after use
- Reshuffle when deck becomes empty

---

## Get Out of Jail Free Cards

- Track card ownership
- Remove card from deck while held
- Return card to discard pile when used

---

## Landing Statistics

Track:

- Total turns simulated
- Landing count for each space
- Landing percentage for each space

---

## Simulation Runs

For BOTH Jail Strategies:

Run 10 independent simulations at:

- 1,000 turns
- 10,000 turns
- 100,000 turns
- 1,000,000 turns

Total datasets:

- 40 datasets for Strategy A
- 40 datasets for Strategy B
- 80 datasets overall

---

## Output

Program output will include:

### Raw Counts

Example:

GO: 24195

### Percentages

Example:

GO: 2.4195%

### Run Summary

Identify:

- Top 3–5 most-landed-on spaces
- Comparison between jail strategies
- Any anomalies or unexpected results

---

# Out of Scope

The following Monopoly mechanics will NOT be implemented.

## Money

Not tracked.

Examples:

- Collecting $200
- Paying taxes
- Rent payments
- Property costs

---

## Property Ownership

Not tracked.

Examples:

- Buying properties
- Selling properties
- Mortgaging

---

## Auctions

Not implemented.

---

## Houses and Hotels

Not implemented.

---

## Trading

Not implemented.

---

## Multiple Players

Only a single player will be simulated.

---

## Bankruptcy

Not implemented.

---

## Winning or Losing

The simulation will not determine winners.

---

## Assumptions

1. Only player movement affects landing probabilities.
2. Money-related game mechanics do not significantly impact movement probabilities.
3. A single player is sufficient for estimating long-run landing probabilities.
4. Random

# Possible Solution Approaches

At the time this document was created, the team has not yet selected a final implementation strategy. The following approaches are identified as possible ways to model and solve the Monopoly simulation problem. Final design decisions will be made by the implementation lead.

---

## Procedural Design

One possible solution would be to use a procedural design centered around functions and shared data structures.

Possible implementation ideas include:

- Functions for dice rolling
- Functions for movement and turn handling
- Arrays or lists to represent the Monopoly board
- Separate functions for Chance and Community Chest behavior
- Arrays to store landing statistics

### Potential Advantages

- Simpler initial implementation
- Fewer classes and files required
- Easier for small prototypes

### Potential Challenges

- Rules may become scattered across multiple functions
- May become harder to maintain as complexity increases
- Testing individual components could be more difficult

---

## Object-Oriented Design

Another possible solution would be to model Monopoly using classes and objects.

Possible objects could include:

- Board
- Square
- Player
- Deck
- Card
- Simulation Runner
- Statistics Collector

### Potential Advantages

- Clear separation of responsibilities
- Easier to model real-world Monopoly concepts
- May improve maintainability and code organization

### Potential Challenges

- Requires additional planning and design
- More files and classes to manage

---

## Board Representation Options

Several methods could be used to represent the Monopoly board.

### Option A: Array or List Representation

Store board spaces in a fixed ordered structure.

Example:

```text
0 = GO
1 = Mediterranean Avenue
2 = Community Chest
...
39 = Boardwalk
```

#### Potential Advantages

- Simple indexing
- Efficient movement calculations
- Easy statistical tracking

---

### Option B: Individual Space Objects

Represent each Monopoly square as its own object containing data such as:

- Name
- Type
- Landing count

#### Potential Advantages

- Flexible design
- Easy to extend

#### Potential Challenges

- Increased implementation complexity

---

## Chance and Community Chest Deck Management

Several approaches may be used for card behavior.

### Option A: Random Draws

Select a random card whenever a draw is needed.

#### Potential Advantages

- Easy implementation

#### Potential Challenges

- May not accurately model deck behavior

---

### Option B: Shuffled Decks with Discard Piles

Maintain a shuffled deck, draw cards in order, place used cards into a discard pile, and reshuffle when necessary.

#### Potential Advantages

- Closely resembles physical gameplay
- Supports more realistic simulation behavior

#### Potential Challenges

- Requires additional deck management logic

---

## Jail Strategy Implementation

Because the project requires two jail-exit strategies, several implementation approaches are possible.

### Option A: Shared Conditional Logic

Handle both strategies inside the same turn-processing code using conditional statements.

### Option B: Separate Strategy Components

Implement each jail strategy separately and compare results across runs.

#### Potential Advantages

- Easier comparison of behavior
- Cleaner separation of strategy logic

#### Potential Challenges

- Additional design effort

---

## Data Collection Approaches

Several methods may be used to track and store results.

Possible options include:

- In-memory arrays
- Lists or collections
- CSV output files
- Text-based reports

The final implementation may use one or a combination of these methods depending on team preference and reporting needs.

---

# Potential Challenges

The team identified several areas that may require additional investigation regardless of the final design approach.

- Implementing all required movement rules correctly
- Handling Chance and Community Chest card actions
- Managing Get Out of Jail Free cards
- Tracking consecutive doubles accurately
- Ensuring players are sent to Jail under the correct conditions
- Producing and storing large amounts of simulation data
- Verifying that simulation results appear reasonable as the number of turns increases

These challenges will be considered during planning, implementation, testing, and verification phases of the project.
