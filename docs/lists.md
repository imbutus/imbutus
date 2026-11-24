# lists

Lists are the universal data container: one ordered, reusable set of items any command can work through — targets to scan, pages to test, hosts to watch — with optional properties on every item.

| Action | How |
|---|---|
| Attach a list to a command | `--list <id>` |
| Create from a file | `findings list-save --list l-<id> --kind targets --file <path>` on the machine |
| Filter one list into another | `findings list-filter --from <src> --to <dst> --where 'status=done,prof<7,sec<7'` |
| Judge every host in a list | `weakness --list <id>` |
| Hack every host in a list | `hack --list <id>` |

- The input list is never changed by a command; a run writes results to its items.
- A re-run takes only the items that are not finished.
- Every item carries its own status and its own result.
