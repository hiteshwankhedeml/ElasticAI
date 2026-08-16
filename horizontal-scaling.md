# Horizontal Scaling

* Horizontal scaling distributes requests across instances, so a single instance failure or restart doesn't take the app offline.
* Azure Databricks rolls a new deployment out to a build instance first, and only updates the remaining instances after that build instance succeeds.
* Session affinity routes every request from the same user to the same instance whenever possible.
* Your app must listen on `0.0.0.0` (not `127.0.0.1` or `localhost`).
* App ⇒ Configure ⇒ Enable Horizontal scaling ⇒ Specify number of instances
