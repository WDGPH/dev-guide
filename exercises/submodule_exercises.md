# WDGPH Submodule Demo — Hands-On Exercises

This exercise set mirrors the live demo. Developers will practice cloning a repo, running `viper`, removing templates, and re‑cloning the `phu_templates` submodule.

---

## Exercise 1 — Clone the Repository

```sh
git clone https://github.com/WDGPH/immunization-charts-python
```

Move into the directory:

```sh
cd immunization-charts-python
```

---

## Exercise 2 — Run VIPER With the Default Templates

Use the provided test dataset:

```sh
uv run viper rodent_dataset.xlsx en
```

Verify that output PDFs were created successfully.

---

## Exercise 3 — Remove the Templates Folder

This is a placeholder for where the submodule will go, but needs to first be removed. It cannot be simply replaced

```sh
rm -r phu_templates
```

Confirm the folder is gone:

```sh
ls
```

---

## 📦 Exercise 4 — Re‑Clone the `phu_templates` Submodule

Clone the template library with all its submodules:

```sh
git clone --recurse-submodules https://github.com/WDGPH/phu_templates
```

Move into the cloned repo:

```sh
cd phu_templates
```

List its contents:

```sh
ls
```

Check Git status:

```sh
git status
```

Move back to the main repo:

```sh
cd ..
ls
```

Move up once more if needed:

```sh
cd ..
```

---

## Exercise 5 — Run VIPER Again Using a PHU-specific Templates

This simulates specifying a template source manually:

```sh
uv run viper --templates <phu_acronym> en
```

Ensure output files are created and the pipeline runs correctly.

---

## Exercise 6 - Create a New Directory in the Submodule and Update the Pointer 

In this exercise, you will simulate a real workflow:
A developer adds a new folder (e.g., a new PHU, a new locale, new assets) to the phu_templates repository, commits the change, and then updates the parent repo’s submodule pointer.

This is the exact workflow for maintaining shared, governed templates across PHUs.

### Step 1 — Move Into the Submodule

From the parent repository:

```sh
cd phu_templates
```

Confirm you are inside the submodule:

```sh
git status
```

You should see a clean working tree.

### Step 2 — Create a New Directory

Example: adding a new template folder for a fictional PHU:

```sh
mkdir demo_phu
echo "Demo PHU template placeholder" > demo_phu/README.md
```

Confirm the new folder exists:

```sh
ls
```

### Step 3 — Commit the Change to the Submodule Itself

```sh
git add .
git commit -m "Add demo_phu directory for exercise"
```

(This updates the submodule repo, not the parent.)

To verify:

```sh
git log --oneline -1
```

### Step 4 — Move Back to the Parent Repo
```sh
cd ..
```

List files to confirm you're back in the main project:

```sh
ls
```

### Step 5 — Update the Submodule Pointer in the Parent Repo

The parent repo must record that the submodule is now pointing at a new commit.

```sh
git add phu_templates
git commit -m "Update submodule pointer after adding demo_phu"
```

### Step 6 — (Optional) Push Both Repos

Push the submodule changes:

``` sh
cd phu_templates
git push
cd ..
```
