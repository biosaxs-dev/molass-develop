(coding_style)=
# Coding Style

## Key Points
We state here what style, we believe, is desirable in coding `Molass Library`. Stated in mottos:

* Be researcher friendly
* Namely, for example, avoid certain advanced language features
* Why-oriented docstring documentation

## Elaboration with GitHub Copilot
Here are some hints from chats with GitHub Copilot.

`Molass Author`: If I say "why-oriented docstring documentation" to suggest our coding style, does that make any sense to you?

`GitHub Copilot`: Yes, "why-oriented docstring documentation" makes sense as a coding style concept. It suggests that your docstrings should focus on explaining why a piece of code exists or behaves a certain way, rather than just describing what it does or how it works. This approach can be particularly helpful for researchers or developers who need to understand the reasoning behind decisions in the code, which is often more valuable than just understanding the mechanics.

Example: Linear Search Instead of Binary Search

```python
def find_element(elements, target):
    """
    Finds the index of the target element in the list using linear search.

    This function uses linear search instead of binary search because the input
    list is expected to be small and unsorted. Sorting the list for binary search
    would add unnecessary overhead in this specific use case.
    """
    for i, element in enumerate(elements):
        if element == target:
            return i
    return -1
```

This approach provides context and rationale, making the code more understandable and maintainable.

Some other questions to ask GitHub Copilot:

`Molass Author`: Do you have any other advice for making our coding style researcher-friendly?

`Molass Author`: I mean researcher-friendly here that you should be aware of the fact that the developers or maintainers may be researchers, and not necessarily professional programmers. In this sense, I think we should avoid some advanced language features. Do you agree? If so, I would appreciate it if you could give a few examples of such features to avoid.

To the above questions, `GitHub Copilot` would give several more suggestions, which we omit here, implying you can ask anytime if you know what to ask. 

Acknowledgement to:
Suggestions provided by GitHub Copilot, an AI programming assistant.