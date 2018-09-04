
# Author : Om Guru Naresh Sreenivasan

'''Assignment 1
Please add your code where indicated. You may conduct a superficial test of
your code by executing this file in a python interpreter.
The documentation strings ("docstrings") for each function tells you what the
function should accomplish. If docstrings are unfamiliar to you, consult the
Python Tutorial section on "Documentation Strings".
'''

import math
import random

def square(n):
    """Calculate the square of a number.
    Args:
        n: An integer or a real number to be squared.
    Returns:
        he square of the number `n`
    """
    # YOUR CODE HERE
    return n*n


def cube(n):
    """Calculate the cube of a number.
    Args:
        n: An integer or a real number to be cubed.
    Returns:
        The cube of the number `n`
    """
    # YOUR CODE HERE
    return n*n*n


def is_capitalized(word):
    """Return True if word starts with capital letter else False.
    Args:
        word: A string
    Returns:
        True if word starts with capital letter else False.
    """
    # YOUR CODE HERE
    if word[0].isupper():
        return True
    else:
        return False
    


def spell_chicago():
    """Print the characters in the word "Chicago" one character per line.
    This function should print out the characters in "Chicago". If
    one runs this function one would see something like::
        C
        h
        i
        c
        a
        g
        o
    You are strongly encouraged to use a ``for`` loop in this function.
    """
    # YOUR CODE HERE
    
    for i in 'Chicago':
        print(i)
        


def character_proportion(character, text):
    """Calculate the proportion of characters in text which are `character`.
    The character "o" occurs twice in the six-character string "Boston". Thus
    the proportion of characters which are "o" is one third.
    Args:
        character: A character (aka a string of length 1) such as "o".
        text: A string.
    Returns:
        float: The proportion of characters in `text` which are `character`.
    """
    # YOUR CODE HERE
    char_count=0
    for i in text:
        if i==character:
          char_count=char_count+1
        else:
            continue
    return char_count/len(text)
    


def random_sum(n):
    """Calculate the sum of `n` random numbers.
    This is an artificial exercise to introduce you to the Python ``random``
    module.
    Draw `n` numbers from between 0 and 1 and return their sum.
    Args:
        n: A non-negative integer.
    Returns:
        float: The sum of `n` random numbers.
    """
    # YOUR CODE HERE
    sum_random_numbers=0
    for i in range(n):
        sum_random_numbers=sum_random_numbers+random.randint(0,1)
    return sum_random_numbers

# Challenge exercise
def character_proportion_monte_carlo(character, text, n):
    """Calculate the proportion of characters in text which are `character` using random sampling.
    See the docstring for `character_proportion` for an introduction.
    In very long texts (e.g., all of Wikipedia) calculating the proportion of
    characters which are a given character is costly. It is less costly to
    estimate the proportion by randomly sampling characters from the text and
    calculating the proportion of characters in the random sample which are the
    given character.
    Take `n` characters uniformly at random (sample *with replacement*) from
    `text` and return the proportion of these `n` characters which are
    `character.
    Args:
        character: A character (aka a string of length 1) such as "o".
        text: A string.
        n: An integer greater than 0.
    Returns:
        float: The *estimated* proportion of characters in `text` which are `character`.
    """
    # YOUR CODE HERE
    char_count=0
#    n=random.sample()
    ran_sam=random.sample(text,n)
    for i in ran_sam:
#    for i in text:
        if i==character:
          char_count=char_count+1
        else:
            continue
    return char_count/len(ran_sam)
    


# DO NOT EDIT CODE BELOW THIS LINE

import unittest


class TestAssignment1(unittest.TestCase):

    def test_square1(self):
        self.assertEqual(square(5), 25)
        self.assertEqual(square(10), 100)

    def test_cube1(self):
        self.assertEqual(cube(2), 8)

    def test_is_capitalized(self):
        self.assertTrue(is_capitalized('Hello'))
        self.assertFalse(is_capitalized('hello'))

    def test_spell_chicago1(self):
        self.assertIsNone(spell_chicago(), None)

    def test_character_proportion1(self):
        self.assertGreater(character_proportion('o', 'Boston'), 0)
        self.assertLess(character_proportion('o', 'Boston'), 1)
        self.assertEqual(character_proportion('o', 'Boston'), 1/3)

    def test_random_sum1(self):
        self.assertIsNotNone(random_sum(100))
        self.assertGreater(random_sum(100), 0)
        self.assertGreater(random_sum(1000), 5)

    def test_character_proportion_monte_carlo1(self):
        self.assertGreaterEqual(character_proportion('o', 'Boston'), 0)
        self.assertLessEqual(character_proportion('o', 'Boston'), 1)
        self.assertGreaterEqual(character_proportion_monte_carlo('o', 'Boston', 6), 0)

if __name__ == '__main__':
    unittest.main()
