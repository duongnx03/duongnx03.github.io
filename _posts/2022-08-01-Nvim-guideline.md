# Neovim guideline
## Basic command lines

**Open a project following path**
```bash
  nvim <folder_path>
```

**Create a new file in Neovim tree**
```bash
1. moving the cursor under the folder
2. press the "a" key
3. input the file name
4. enter
```

**Close the current buffer**
```bash
:q
```

**Toggle the tree of the folder in neovim**

```bash
# in neovim normal mode use:
Ctrl + n 
```

**Switch between buffers**
* ctrl+l :to navigate to the  right buffer
* ctrl+h :to navigate to the left buffer

**Open file in the horizontal split windown in Vim**

```bash
Move the cursor under the file that you want to open

Then use <C-v> to open file in vertical and <C-x> to open file in horizontal.
```

or use vim command
```bash
:split %:h

<TAB>

Then select the file using Ctrl+n or previous file use Ctrl+p

Enter
```

## Install a plugin in neovim use Packer and Nvchad format.

Reference to [Nvchad](https://nvchad.github.io/config/plugins)
