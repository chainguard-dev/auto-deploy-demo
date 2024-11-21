# Auto Update a Helm Deployment

* Monitor for new Chainguard Images in your dedicated registry
* Verify integrity of the image by validating the digital signature with cosign
* Use chainctl image diff to determine if the new image remediates a Critical or High CVE
* Scan the image with grype
* Create a PR that:
  * Updates Helm with new image
  * Lists the CVEs that will be remediated with the change
  * Attaches the scan result
  * Uses Chainguard Unique Tags for consistency and atomic rollbacks
* Deploy to a Kubernetes Cluster once PR is merged
* Adheres to security least privilege by using short-lived ephemeral tokens to:
  * Authenticate to the Chainguard Registry using an [assumed identity](https://edu.chainguard.dev/chainguard/administration/iam-organizations/assumable-ids/) (using the ambient creds of each workflow invocation)
  * Authenticate to GitHub (using [octo-sts](https://www.chainguard.dev/unchained/the-end-of-github-pats-you-cant-leak-what-you-dont-have) in place of a long-lived PAT) 
  * Signs commits using [Sigstore/gitsign](https://docs.sigstore.dev/cosign/signing/gitsign/)
 
## Usage

* Run the scan workflow will populate the scan data for the very old redis-server-bitnami image: ![image](https://github.com/user-attachments/assets/ebdaca95-efbd-4fe2-a7f1-3b61d782466a)
* Run the updates workflow to generate a PR with the fixes and scan results: ![image](https://github.com/user-attachments/assets/62dee720-e592-488d-836b-2364dc8e8729)
* Merge
* Profit ![image](https://github.com/user-attachments/assets/3b8e1090-1520-41de-9b2e-7f36b0a464f0)

