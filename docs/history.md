# compat history

Checks collected from live Computer sandboxes, grouped by image. Live copy:
<https://pplx-proxy-notes.vercel.app/docs/history>

| image | python | kernel | workspaces | checks | status |
| --- | --- | --- | --- | --- | --- |
| `computer/2026.09` | 3.14 | `6.1.155+` | 23 | 84 | pass |
| `computer/2026.08` | 3.13 | `6.1.141` | 31 | 142 | pass |
| `computer/2026.07` | 3.13 | `6.1.141` | 18 | 67 | partial |
| `computer/2026.06` | 3.12 | `6.1.112` | 9 | 29 | partial |

## Notes

- `2026.09` reports its kernel as `6.1.155+`. The trailing `+` is new and breaks anything
  parsing the release string into integers.
- `SANDBOX_IMAGE_TAG` is unset on `2026.09`, so checks from that image resolve their
  runtime as `computer/unknown` unless the reporter names it.
- The connector schema is not versioned in any way the sandbox can read, so schema drift
  only shows up as a mismatch between two workspaces on the same image.
