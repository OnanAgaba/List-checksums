# List-checksums

Consider a list, each of whose zero or more elements are integers or other lists. Those other lists themselves may
contain zero or more integers and zero or more lists, which may themselves contain zero or more integers and
zero or more lists, ad infinitum. We will call such entities number trees.
We can calculate a “checksum” for a number tree by summing all the integers found in its outermost list and any
lists contained within, weighted by their list depth (i.e. by howmany lists-within-lists they are contained in). This
means that if a number is found in the outermost list, it is multiplied by one before being added to the sum, if it
is directly within a list within the outermost list, it is multiplied by two before being added to the sum, etc. Here
are some examples:

| List Name | Structure                             | Expected Checksum |
| --------- | ------------------------------------- | ----------------- |
| `list1`   | `[]`                                  | `0`               |
| `list2`   | `[1]`                                 | `1`               |
| `list3`   | `[[1]]`                               | `2`               |
| `list4`   | `[[[5]]]`                             | `15`              |
| `list5`   | `[[], [], []]`                        | `0`               |
| `list6`   | `[1, [1], [[1]]]`                     | `6`               |
| `list7`   | `[1, 4, [], -3, [0, 14, [1]], 0, 10]` | `43`              |


Several number trees (how many is unknown to you) like those above will have been saved into a file called
numbertrees.pickle using the the Python pickle package (https://docs.python.org/3/library/pickle.html),
and calling pickle.dump() once for each number tree. Your task is calculate the checksum for all well-defined
number trees in the file (you will need to call pickle.load() repeatedly) and print each one to the screen, one
per line. Exit gracefully (without crashing) when there are no more number trees in the pickle file.
