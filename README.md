# Overview

This is a patholigical example to show why `git merge` is better than `git rebase`.

The claim is that `git merge` has a better worst case number of conflicts than `git rebase`.

# Demo

## Merge

Checkout branch `origin/stuff` as `merge`:

```shell
git checkout -b merge origin/stuff
```

Now merge in `origin/main`:

```shell
git merge origin/main
```

You must now resolve the conflict:

```shell
git mergetool
```

> ℹ️  The result must be an ordered list with only the items from 'theirs' and 'ours'.

The result should be:
```text
0, 1, 2, 3, 4, 5, 6, 7, 8, 9
```

Note how there was only a single conflict.

Commit:

```shell
git commit
```

## Rebase


Checkout branch `origin/stuff` as `rebase`:

```shell
git checkout -b rebase origin/stuff
```

Now rebase onto `origin/main`:

```shell
git rebase origin/main
```

You must now resolve the conflicts:

```shell
git mergetool
```

> ℹ️  The result must be an ordered list with only the items from 'theirs' and 'ours'.

The result of the first conflict should be:
```text
0, 1
```

The result of the second conflict should be:
```text
0, 1, 2
```

The result of the third conflict should be:
```text
0, 1, 2, 3
```

...

You get the point.
