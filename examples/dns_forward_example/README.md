# Simple Example

This example illustrates how to reserve multiple IP addresses at the same
time, and how to enable the Google Cloud DNS registration functionality that
will register the IP addresses and their corresponding DNS names with Google
Cloud DNS.

[^]: (autogen_docs_start)


## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| credentials_path | The path to a Google Cloud Service Account credentials file | string | - | yes |
| dns_domain | The name of the domain to be registered with Cloud DNS | string | - | yes |
| dns_managed_zone | The name of the managed zone to create records within.  This managed zone must exist in the host project. | string | - | yes |
| dns_project | The project where DNS A records will be configured. | string | - | yes |
| dns_short_names | A list of DNS short names to register within Cloud DNS.  Names corresponding to addresses must align by their list index position in the two input variables, `names` and `dns_short_names`.  If an empty list, no domain names are registered.  Multiple names may be registered to the same address by passing a single element list to names and multiple elements to dns_short_names.  (e.g. ["gusw1-dev-fooapp-fe-0001-a-001"]) | list | - | yes |
| names | A list of IP address resource names to create.  This is the GCP resource name and not the associated hostname of the IP address.  Existing resource names may be found with `gcloud compute addresses list` (e.g. ["gusw1-dev-fooapp-fe-0001-a-001-ip"]) | list | - | yes |
| project_id | The project ID to deploy to | string | - | yes |
| region | The region to deploy to | string | - | yes |
| subnetwork | The subnet containing the address.  For EXTERNAL addresses use the empty string, "".  (e.g. "projects/<project-name>/regions/<region-name>/subnetworks/<subnetwork-name>") | string | - | yes |

## Outputs

| Name | Description |
|------|-------------|
| addresses | List of address values managed by this module (e.g. ["1.2.3.4"]) |
| credentials_path | Path to credentials file being used |
| dns_fqdns | List of DNS fully qualified domain names registered in Cloud DNS.  (e.g. ["gusw1-dev-fooapp-fe-0001-a-001.example.com", "gusw1-dev-fooapp-fe-0001-a-0002.example.com"]) |
| forward_zone | The GCP name of the forward lookup DNS zone being used |
| names | List of address resource names managed by this module (e.g. ["gusw1-dev-fooapp-fe-0001-a-0001-ip"]) |
| project_id | ID of the project being used |
| region | Region being used |

[^]: (autogen_docs_end)

To provision this example, run the following from within this directory:
- `terraform init` to get the plugins
- `terraform plan` to see the infrastructure plan
- `terraform apply` to apply the infrastructure build
- `terraform destroy` to destroy the built infrastructure