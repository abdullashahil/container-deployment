# Assessment evidence
## Environment and source revision
## Architecture/request-path diagram
## Original issue -> diagnosis -> fix -> verification -> limitation
| Task | Original observation | Diagnosis | Repair | Actual command/output | Limitation |
|---|---|---|---|---|---|
| 1 |``` ERROR: failed to build: failed to solve: failed to compute cache key: failed to calculate checksum of ref u06340iq4oh1zbezb3hvnhgv4::x2av19onvsjzuk9sc331g9i8a: "/requirements-missing.lock": not found ```| Fix the incorrect dependency-file path in Dockerfile| Fix the incorrect dependency-file path from requirements-missing.lock to requirements.lock| Building 0.1s (14/14) FINISHED, {"status": "ok"}| |
| 2 |```Error response from daemon: No such image: container-deployment:1.0.O``` |Repair scripts/load-image.sh so it builds/tags and loads the exact image expected by the supplied kind cluster. | changed 1.0.O to 1.0.0|successful | |
| 3 | "app": "cloudnote"| wrong Service selectors| change "app": "cloudnote" to "app": "cloudnotes"| successful| |
| 4 | Deployment reference to a undefined AP_MODE| Fix the Deployment reference to the existing APP_MODE key without hardcoding configuration in the image. | key changed from  "key": "AP_MODE" to  "key": "APP_MODE"| configured mode is reported by /info and a saved note survives replacement of the single application Pod.| |
| 5 | A failing health/notes test returns reporting success.| Fix scripts/verify-release.sh so a failing health/notes test returns nonzero rather than reporting success.| removed ``` true``` from verify-release.sh | ```urllib.error.URLError: <urlopen error [Errno 61] Connection refused>```| |
## Remaining risk and reproducible rebuild/cleanup
