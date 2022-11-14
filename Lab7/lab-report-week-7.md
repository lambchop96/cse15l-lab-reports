# Week 7 Lab Report - Vim

## Changing the name of the `start` parameter and its uses to `base` in `DocSearchServer.java`:

`/star<Enter>cebase<Esc>n.n.:w<Enter>`

---

`/star<Enter>`

The `/` allows us to search for a pattern; in this case, we search for `start` since that is the word we are trying to replace. However, just typing `star` is sufficient to bring the cursor to the correct location at the beginning of the word `start` in the `getFiles` function signature. Pressing `<Enter>` then finalizes what we are searching for and returns us to normal mode.

![star-enter](star-enter.png)

---

`ce`

`c` stands for change. After typing `c`, we type `e` so that it deletes from the cursor to the end of the word, effectively removing `start`. `c` also puts us in insert mode after typing in the cursor movement command (in this case, `e`) so that we can replace `start` with whatever we want.

![ce](ce.png)

---

`base<Esc>`

Since we are in insert mode, we type `base` into where `start` once was. Then, we press `<Esc>` to return to normal mode.

![base-esc](base-esc.png)

---

`n.`

Next, we type `n` which goes to the next occurrence of `star` since Vim still remembers that we are looking for that pattern. This moves the cursor one line down to the beginning of `start`. Pressing `.` causes Vim to repeat the last change to the file done, and that is `cebase<Esc>`. Notice that it doesn't repeat the last command, but the last actual change to the file. You cannot repeat movement commands using this command. Folloinwg `n.`, the second `start` is now replaced by `base`.

![n-dot1](n-dot1.png)

---

`n.` (_again_)

Now, we type `n.` again so that we move the cursor to the beginning of the third `start` and it is replaced with `base`.

![n-dot2](n-dot2.png)

---

`:w`

Lastly, as we are in normal mode, we type `:w` which writes the changes we made so that they are saved.

![write](write.png)

---

---

Editing the file in VS Code then scp-ing the repository over to the remote server took **21 minutes and 4 seconds** or **1264 seconds**. This is because just scp-ing the repository and all of its files (especially those in the `technical` directory) took about 20 minutes. The first time I tried it, it actually froze on a file during the copy and never finished.

Editing the file on the remote server using Vim took **40 seconds**, and nearly half of that time was spent running the bash script to run the tests. The process went very smoothly and nothing took too long.

Personally, I much prefer the second style as it is far faster not having to do the scp step. In addition, being adept at the Vim commands makes using the keyboard somewhat faster than using the mouse. Being able to repeat previous actions with `.` made replacing the multiple occurrences of `start` quite fast. However, if one is not so familiar with Vim, editing in VS Code is still faster than using Vim.

My decision on choosing whether to use the first method or the second method depends on if a remote server is involved. If we have to scp to a remote server, I would much rather use Vim and directly modify it on the remote server instead of editing it in VS Code then spending 20 minutes waiting for the scp to finish. It also depends on how efficiently I can use the Vim commands. As I am not so familiar with Vim, I tend to use VS Code to make edits rather than Vim because I don't instinctively understand all the Vim commands yet.
