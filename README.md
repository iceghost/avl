# AVL Tutorial

This is an AVL tutorial.

Let's start by initializing a hello world program:

```diff
e6bb367ab9a48c869d38f2acb8c55ae270a51719

diff --git a/main.c b/main.c
new file mode 100644
index 0000000..44b9c78
--- /dev/null
+++ b/main.c
@@ -0,0 +1,6 @@
+#include <stdio.h>
+
+int main() {
+       printf("hello world!\n");
+       return 0;
+}
```

```console
$ gcc main.c -o main
$ ./main
hello world!
```

To avoid typing those commands, let's put them in a Makefile:

```diff
0861355cb9120a438e094ed49224fbf4f35f60e8
diff --git a/Makefile b/Makefile
new file mode 100644
index 0000000..742dabb
--- /dev/null
+++ b/Makefile
@@ -0,0 +1,5 @@
+run: main
+       ./main
+
+main: main.c
+       gcc main.c -o main
```

```console
$ make
./main
hello world!
```

```console
$ rm main
$ make
gcc main.c -o main
./main
hello world!
```

First, make `run` a `PHONY` target.

```diff
16305c382407243ef2d5598f0f88279d5368b5a2
diff --git a/Makefile b/Makefile
index 742dabb..c74da22 100644
--- a/Makefile
+++ b/Makefile
@@ -1,3 +1,4 @@
+.PHONY: run
 run: main
        ./main
```

This means `run` isn't a file, as opposed to `main`.

Silence the commands:

```diff
c95e605c569280061e76c4058334cb3a52fe651e
diff --git a/Makefile b/Makefile
index c74da22..9cac427 100644
--- a/Makefile
+++ b/Makefile
@@ -1,6 +1,6 @@
 .PHONY: run
 run: main
-       ./main
+       @./main

 main: main.c
-       gcc main.c -o main
+       @gcc main.c -o main
```

```console
$ make
hello world!
```

Much better now.
