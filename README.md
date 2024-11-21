# Auto Update / Deploy Helm Demo

* Monitor for new Chainguard Images in your dedicated registry
* Use chainctl image diff to determine if the new image remediates a Critical or High CVE
* Create a PR that updates Helm with the new image tag
* Leverage Chainguard Unique Tags for consistency and atomic rollbacks

This demo adheres to security least privilege by using short-lived ephemeral tokens to:
* Authenticate to the Chainguard Registry using an [assumed identity](https://edu.chainguard.dev/chainguard/administration/iam-organizations/assumable-ids/) (using the ambient credentials of each workflow invocation)
* Authenticate to GitHub (using [octo-sts](https://www.chainguard.dev/unchained/the-end-of-github-pats-you-cant-leak-what-you-dont-have) in place of a long-lived PAT) 
* Signs commits using [Sigstore/gitsign](https://docs.sigstore.dev/cosign/signing/gitsign/)
