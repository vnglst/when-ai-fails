# Let them play Set!

Set is a card game where players aim to identify sets of three cards from a layout of 12. Each card features a combination of four attributes: shape, color, number, and shading. A valid set consists of three cards where each attribute is either the same on all three cards or different on each. The goal is to find such sets quickly and accurately.

Even though this game is a solved computer problem (e.g. as an algorithm or with deep learning) I thought it would be interesting to see if Large Language Models are able to figure this out. Turns out they fail miserably at it. But as usual they do it with a lot of confidence!

## Problem description

Here's an example of what the game looks like:

![Example deck](./example-deck.jpeg)

There exists a shorthand notation for describing the attributes of a card. For example, the card in the top left corner of the image above can be described as `O2RS`. Meaning it has two solid red ovals.

The full definition of this notation is:

```
[Shape][Number][Color][Shading]

Shape: O (oval), S (squiggle), D (diamond)
Number: 1, 2, or 3 (count of shapes)
Color: R (red), G (green), P (purple)
Shading: S (solid), O (outline), H (hashed/shaded)
```

Using this notation any deck can be described in text. In this particular layout there are 3 Sets:

1.
2.
3.

Our expection is that either the LLM will be able to identify the sets or at least give an honest answer that it doesn't know to find them.

Failure would be if the LLM starts giving answers that are not sets.

## Prompt

We're going to ask the LLM the following:

```
You are given a layout of Set cards, each represented by a shorthand notation detailing their attributes. Each card can be described using the format: [Shape][Number][Color][Shading]

- Shape: D (diamond), O (oval), S (squiggle)
- Number: 1, 2, or 3 (number of shapes on the card)
- Color: R (red), G (green), P (purple)
- Shading: S (solid), O (outlined), H (hashed/shaded)

The card layout is as follows:

Top row:
1. O2RS (Two solid red ovals)
2. O1PH (One hashed purple oval)
3. O2GS (Two solid green ovals)
4. S1GO (One outlined green squiggle)

Middle row:
5. D3GH (Three hashed green diamonds)
6. S2RS (Two solid red squiggles)
7. D2GO (Two outlined green diamonds)
8. S2GO (Two outlined green squiggles)

Bottom row:
9. D3RH (Three hashed red diamonds)
10. O1PO (One outlined purple oval)
11. O2RH (Two hashed red ovals)
12. O3GS (Three solid green ovals)

Your task is to identify and list all possible Sets from this layout. A Set is a group of three cards where, for each attribute, the cards must all have the same attribute or all different attributes. Provide the sets in terms of their card numbers (e.g., Card 1, Card 2, Card 3).
```

## Results

| Model                          | Can find sets | Comments                                                                                     |
| ------------------------------ | ------------- | -------------------------------------------------------------------------------------------- |
| [`GPT-4o`](./gpt-4o/answer.md) | ❌            | Suggests invalid sets. After verification requests it wrongly states that there are no sets. |
