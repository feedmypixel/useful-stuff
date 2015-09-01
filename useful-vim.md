# Useful Vim Stuff

### Table of contents
- [Copy & Paste](#copy_paste)
- [Edit](#edit)
- [Exit](#exit)
- [Help](#help)
- [Navigation](#navigation)
- [Search](#search)
- [Search & Replace](#search_replace)



<a name="copy_paste">
## Cut/Copy and paste

1. Position the cursor at the beginning of the text you want to cut/copy.
1. Press `v` to begin character-based visual selection, or `V` to select whole lines, or `Ctrl-v` or `Ctrl-q` to select a block.
1. Move the cursor to the end of the text to be cut/copied. While selecting text, you can perform searches and other advanced movement.
1. Press `d` (delete) to cut, or `y` (yank) to copy.
1. Move the cursor to the desired paste location.
1. Press `p` to paste after the cursor, or `P` to paste before.

If you want to change the selected text, press `c` instead of `d` or `y` in step 4. 
In a visual selection, pressing `c` performs a change by deleting the selected text and entering insert mode so you can type the new text.



<a name="edit">
## Edit

#### Insert mode
```
i
```

#### Insert Text
To insert text after or before cursor into a new line. After new line is created the editor is set to insert mode.

```
o,O
```

#### Replace character
When you need to replace only one character under your cursor, without changing to insert mode, use `r`.

```
r
```

#### Delete/cut
You can combine it with movement, e.g. `dw` deletes the first word on the right side of the cursor. It also copies the content.

```
d
```

#### Delete/cut line
```
dd
```

#### Paste
```
p
```

#### Paste before cursor
```
P
```

#### Remove two words
```
d2e
```

#### Remove two words
```
d2w 
```

#### Delete letter at cursor
```
x
```

#### Delete character to left of cursor
```
X
```

Add a number in front of the above commands to repeat the command - `3b` moves you back 3 words. `9l` moves you right 9 letters.

#### Repeat text
> Will write text 'ben' 30 times

```
30iben
```

```
Esc
```

#### Undo
```
u
```

#### Redo
```
ctrl+R
```

#### Repeat the previous command
```
.
```



<a name="exit">
## Exit

#### Save
```
:w
```

#### Quit
```
:q
```

#### Quit without saving
```
:q!
```

#### Save the file to filename
```
:w filename
```



<a name="help">
## Help

#### Bring up help
```
:help
```



<a name="navigation">
## Navigation

#### Visual mode
```
v
```

#### Move forward to start of word
```
w
```

#### Move backward to start of current word then previous word
```
b
```
#### jump to the matching parenthesis or bracket
> In text that is structured with parentheses or brackets (, { or [ use %

```
%
```

#### To reach the beginning of a line
```
0
```

#### Reach end of a line
```
$
```

#### Left
```
h
```

#### Right
```
l
```

#### Up
```
k
```

#### Down
```
j
```

#### Move half-page down
```
d
```

#### Move half-page up
```
u
```

#### Page up
```
b
```

#### Page down
```
f
```

#### Move forward to end of current word then next word
```
e
```

#### Move the cursor word-by-word
> Capital B and E move the cursor word-by-word using only white space as the delimiter

```
B,E
```

#### Beginning of file
```
gg
```

#### End of file
```
G
```

#### Go to line number
To jump directly to a specific line, give its line number along with `G`.

```
100G
```



<a name="search">
## Search

#### Move to the next or previous occurrence of a character
To find and move to the next or previous occurrence of a character, use `f` and `F`, e.g. `fo` finds next 'o'.

```
f,F 
```

#### Find nth occurrence
You can combine `f` with a number. For example, you can find 3rd occurrence of 'q' with `3fq`

```
3fq
```


#### Next occurrence of the word under cursor
```
*
```

#### Previous occurrence of the word under cursor
```
#
```

#### Search
```
/<search_term>
```

#### Next occurrence
```
n
```

#### Previous occurrence
```
N
```



<a name="search_replace">
## Search and replace

#### Find each occurrence of 'foo' (in all lines), and replace it with 'bar'
```
:%s/foo/bar/g
```

#### Find each occurrence of 'foo' (in the current line only), and replace it with 'bar'
```
:s/foo/bar/g
```

#### Change each 'foo' to 'bar', but ask for confirmation first
```
:%s/foo/bar/gc
```

#### Change only whole words exactly matching 'foo' to 'bar'; ask for confirmation
```
:%s/\<foo\>/bar/gc
```

#### Change each 'foo' (case insensitive) to 'bar'; ask for confirmation
```
:%s/foo/bar/gci
```

#### Change each 'foo' (case sensitive) to 'bar'; ask for confirmation
```
:%s/foo/bar/gc
```