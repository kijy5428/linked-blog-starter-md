To show the **Git diff with the previous commit**, you can use the following command:

```bash
git diff HEAD^
```

### 🔍 Explanation:

- `HEAD` refers to the current commit.
- `HEAD^` refers to the **previous commit**.
- `git diff HEAD^` shows the changes **between the previous commit and the current one**.

---

### 🧰 Other Useful Variants

- **Compare with two commits ago:**

```bash
  git diff HEAD~2
```

- **Compare specific files:**

```bash
  git diff HEAD^ -- path/to/file.txt
```

- **Show diff with color and word-level changes:**

```bash
  git diff --color-words HEAD^
```

- **Show diff in a side-by-side format (if you use a pager like `diff-so-fancy` or `delta`):**

```bash
  git diff HEAD^ | delta
```

Would you like help installing a better diff viewer or exporting the diff to a file?