# Container execution — review candidate

The example below uses pt12; select the immutable model image digest assigned to task_id in task-image-map.tsv. Never substitute the old canary0 router. One task per container, batch<=10, global K=4. The simulator runs outside the policy container.

```sh
IMAGE='gnishan123/b1k-submission@sha256:a76256c005327fdf06a184365b8338e088cc9e130923401f2226c8a1e3a0b46c'
docker pull "$IMAGE"
docker run --rm --gpus device=0 --memory=60000000000 --memory-swap=60000000000 \
  --read-only --tmpfs /tmp:rw,exec,size=8g --shm-size=2g \
  --cap-drop=ALL --security-opt=no-new-privileges \
  -p 8000:8000 "$IMAGE" serve --host 0.0.0.0 --port 8000
curl --fail http://127.0.0.1:8000/readyz
```

This is a proposed production invocation, not evidence that exact Docker flags have passed on RunPod. Do not publish a qualification claim until tested. Reserve sufficient host storage for the shared~126 GB compressed base and extracted layers. Do not expose the policy port publicly without the organizers' networking arrangement. HTTP readiness is separate from the evaluation WebSocket protocol.

Use the exact original wrapper/config from the results ZIP. The request schema comes from the official evaluator network_utils; do not invent a new JSON client. Supply only the routed task, maintain rollout history/reset and batch membership as specified by that wrapper. The server does not fabricate actions on failure. Preserve failed episode evidence.
