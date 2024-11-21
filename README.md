# Auto Update / Deploy Helm Demo

This demo shows how chainguard images can be automated to:
* Monitor for new Chainguard Images in your dedicated registry
* Use chainctl image diff to determine if the new image remediates a Critical or High CVE
* Create a PR that updates Helm with the new image tag
* Leverage Chainguard Unique Tags for consistency and atomic rollbacks
