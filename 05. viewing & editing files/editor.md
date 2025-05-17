## Editors

**nano** – Simple Terminal Editor

`nano filename.txt`

```
Ctrl + O → Save

Ctrl + X → Exit

Ctrl + K → Cut line

Ctrl + U → Paste line
```


**vim** – Powerful, Efficient Editor

`vim filename.txt`

```
i → insert mode

Esc → back to command mode

:w → save

:q → quit

:wq → save and quit

dd → delete a line

/search_term → search
```


## File Viewing and Editing

**`cat file.txt`** – Displays file content & Concatenate and Display

**`tac file.txt`** – Displays file content in reverse order.

**`less file.txt`** – Opens a file for viewing with scrolling support.

**`more file.txt`** – Similar to less, but only **moves forward.**

**`head -n 10 file.txt`** – Displays the first 10 lines of a file.

**`tail -n 10 file.txt`** – Displays the last 10 lines of a file.

**`echo 'Hello' > file.txt`** – Writes text to a file, overwriting existing content.

**`echo 'Hello' >> file.txt`** – Appends text to a file without overwriting.


**How do you monitor a log file in real-time?**

A: Use **`tail -f filename.log`** or less +F filename.log

**Q: How do you search for a word in a file but ignore case?**

A: Use **`grep -i "word" filename`**
