## 0.1.2 (Unreleased)

BACKWARDS INCOMPATIBILITIES / NOTES:

 * The `parent_pool` attribute in the `opc_compute_ip_reservation` resource is now `Optional` and not `Required`.

FEATURES:

 * Vendored dependencies to allow isolated compilation of provider [GH-4]

IMPROVEMENTS:

 * Change `parent_pool` to an Optional attribute [GH-2]

BUG FIXES:

 * Correctly export `ip_address` in `opc_compute_ip_address_reservation` ([#14543](https://github.com/hashicorp/terraform/pull/14543))

## 0.1.1 (May 10, 2017)

BACKWARDS INCOMPATIBILITIES / NOTES:

 * Initial Release of OPC Provider
