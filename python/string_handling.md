---
description: Because NLP has strings in it
---

Once you have a giant string, then you need a list of words.

```python
# Splits string of words into list, separated by spaces
line_one = "The sky has given over"
line_one_words = line_one.split()

# Or pass the separator
# Use \n for Newline
# Use \t for Horizontal Tab
authors = "Audre Lorde,Gabriela Mistral,Jean Toomer,An Qi,Walt Whitman,Shel Silverstein,Carmen Boullosa,Kamala Suraiyya,Langston Hughes,Adrienne Rich,Nikki Giovanni"
author_names = authors.split(",")
```


Or, make a bloody sentence again

```python
reapers_line_one_words = ["Black", "reapers", "with", "the", "sound", "of", "steel", "on", "stones"]
reapers_line_one = " ".join(reapers_line_one_words)
```


When you need to strip through a list of strings, then glue them back together:

```python
love_maybe_lines = ['Always    ', '     in the middle of our bloodiest battles  ', 'you lay down your arms', '           like flowering mines    ','\n' ,'   to conquer me home.    ']

love_maybe_lines_stripped = []

for line in love_maybe_lines: 
  love_maybe_lines_stripped.append(line.strip())

love_maybe_full = "\n".join(love_maybe_lines_stripped)
```


Basic replace syntax:

```python
toomer_bio_fixed = toomer_bio.replace("Tomer", "Toomer")
```


