# adapter.doubaoime.organize

A local adapter for Doubao IME text organization. It supports the dedicated `doubaoime-organize` model.

## Runtime

- command: `python3`

Listens only on `127.0.0.1:18232`; vinput manages its process. Offers `GET /v1/models` and non-streaming `POST /v1/chat/completions`. The content of `choices[0].message.content` is a JSON string with one candidate: `{"candidates":["organized text"]}`.

## Configuration

| Variable | Default | Meaning |
| --- | --- | --- |
| `DOUBAOIME_IDENTITY_PATH` | `~/.cache/vinput/doubaoime-stable/identity.json` | The identity file. |
| `DOUBAOIME_PORT` | `18232` | Loopback listening port. |
| `DOUBAOIME_NO_TRAILING_PUNCTUATION` | false | `1`, `true`, or `yes` removes punctuation at paragraph/line endings locally. |

Empty variables select defaults. CLI equivalents are `--identity`, `--port`, and `--no-trailing-punctuation`.

The scene prompt must be `<vinput-asr>\n{{asr}}\n</vinput-asr>` with one candidate, zero context lines, `raw_cand:true`, `raw_prev:true`, and a 10-second timeout. vinput appends its native `## Constraints` instructions; the adapter extracts only the enclosed ASR text and never forwards those instructions upstream. Literal wrapper markers and newlines within the original text are preserved.

## Failure and Cancellation

TTNet encryption keys are fetched dynamically and cached for at most three hours.

Organization has an 8-second total deadline and a 2-second first-event deadline. Timeouts, transport errors, incomplete streams, and no-rewrite responses return the original text. Disconnecting a local request cancels its upstream task.
