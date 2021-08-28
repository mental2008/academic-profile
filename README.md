# Academic-Profile

Three steps to update my academic profile:

1. Modify the source file `index.jemdoc` .
2. Generate `index.html` based on the source file.

```bash
python jemdoc.py index.jemdoc
```

3. Update `index.html` in the server.

```bash
scp index.html lyangbk@ras.cse.ust.hk:~/public_html/
```

Here is the webpage of my academic profile: https://www.cse.ust.hk/~lyangbk/.

