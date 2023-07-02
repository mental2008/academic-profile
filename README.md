# Academic-Profile

Three steps to update my academic profile:

1. Modify the source file `index.jemdoc` .
2. Generate `index.html` based on the source file.

```bash
$ python3 jemdoc.py index.jemdoc
```

3. Update `index.html` in the server.

```bash
$ scp index.html lyangbk@ras.cse.ust.hk:~/public_html/
```

4. Upload `files` folder.

```bash
$ scp files lyangbk@ras.cse.ust.hk:~/public_html/
```

Here is the webpage of my academic profile: https://www.cse.ust.hk/~lyangbk/.

---

The permissions should be set appropriately.
* The home directory has to be at least world-accessible, i.e., `chmod 701 ~`.
* The same for "public_html" directory, i.e. `chmod 701 ~/public_html`.
* The files under "public_html" directory should be world-readable, i.e.`chmod 604 ~/public_html/*.html`.
