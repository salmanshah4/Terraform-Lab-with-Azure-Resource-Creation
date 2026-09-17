# Terraform-Lab-with-Azure-Resource-Creation
### Objective

Use Terraform in Azure Cloud Shell to create a resource group, virtual network, subnet, and network security group, verify the resources in Azure, and then cleanly destroy them when finished. This SOP provides a repeatable workflow for infrastructure-as-code testing in Azure.

### Link to Loom

<https://loom.com/share/c7188f1d926a465b93c3777555994987>

### Key Steps


**1. Open Azure Cloud Shell and prepare the workspace** [0:15](https://loom.com/share/c7188f1d926a465b93c3777555994987?t=15)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b0bf0d0a-ef9c-48bb-9abc-89f7ca18de47" />

- Sign in to the Azure portal and open **Cloud Shell** from the Home page.
- Reconnect Cloud Shell if prompted.
- Confirm you are in the terminal environment before running commands.
- Create a working directory named `Terraform`.
- Change into the `Terraform` directory so all files are kept together.

 

**2. Create the Terraform configuration file** [1:12](https://loom.com/share/c7188f1d926a465b93c3777555994987?t=72)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/887ae84d-7836-4a21-bb69-4cef5de83a6d" />

- Create a new Terraform file in the working directory.
- Add the Terraform configuration code for the following resources: 
  - **Provider** configuration
  - **Resource Group**
  - **Virtual Network (VNet)**
  - **Subnet**
- Save the file before running any Terraform commands.
- Verify the file contains the intended resource definitions before proceeding.

 

**3. Initialize Terraform and download provider plugins** [2:00](https://loom.com/share/c7188f1d926a465b93c3777555994987?t=120)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bb84ee6d-923a-4570-b4dd-0580f8b26646" />

- Run `terraform init` to initialize the working directory.
- Allow Terraform to download the required provider plugins.
- Confirm Terraform creates the local backend and supporting files needed to manage the configuration.
- Use this step whenever the configuration is first created or when provider setup changes.

 

**4. Review the planned infrastructure changes** [2:50](https://loom.com/share/c7188f1d926a465b93c3777555994987?t=170)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/11f75ee8-45af-41e1-94ae-31bfa9a4e094" />

- Run `terraform plan` to preview what Terraform will create.
- Review the output carefully to confirm it includes the expected: 
  - Resource group
  - Virtual network
  - Subnet
- Use the plan output to catch mistakes before making changes in Azure.
- Do not apply changes until the plan matches the intended design.

 

**5. Apply the Terraform configuration and confirm the deployment** [3:17](https://loom.com/share/c7188f1d926a465b93c3777555994987?t=197)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/65193fe2-f700-4971-b10c-23410ec74afc" />

- Run `terraform apply` to begin creating the resources.
- When prompted, type `yes` to confirm the deployment.
- Wait for Terraform to finish provisioning the resources.
- Treat the confirmation prompt as a final safety check before changes are made in Azure.

 

**6. Verify the created resources in Azure** [4:25](https://loom.com/share/c7188f1d926a465b93c3777555994987?t=265)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f35b1f93-5d50-48b5-ad19-a7b9b76f591b" />

- Open the Azure portal and navigate to **Resource Groups**.
- Confirm the resource group exists.
- Check that the **VNet** and **Subnet** were created successfully.
- Compare the Azure portal results with the Terraform configuration to ensure the deployment matches expectations.

 

**7. Add and deploy a Network Security Group** [5:10](https://loom.com/share/c7188f1d926a465b93c3777555994987?t=310)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d0fb8a79-f164-409e-9c12-e8d55c9da550" />

- Update the Terraform configuration to include a **Network Security Group (NSG)**.
- Save the file after adding the new resource definition.
- Run `terraform plan` again to preview only the new change.
- Run `terraform apply` and type `yes` when prompted.
- Wait for the NSG to finish creating, then verify it appears in the resource group.

 

**8. Destroy the Terraform-managed resources** [6:30](https://loom.com/share/c7188f1d926a465b93c3777555994987?t=390)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/cbeaf6f6-c917-45fb-8635-3e67f70b94d1" />

- Run `terraform destroy` when the lab is complete.
- Review the destruction prompt carefully.
- Type `yes` to confirm removal of the Terraform-managed resources.
- Wait until Terraform reports that all resources have been destroyed.

 

**9. Confirm cleanup in Azure** [7:47](https://loom.com/share/c7188f1d926a465b93c3777555994987?t=467)

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/15b348eb-3ed6-475a-bb67-fbc177bcb593" />

- Return to **Resource Groups** in the Azure portal.
- Confirm the resource group and all associated resources are gone.
- Use this final check to ensure no test resources remain active.
- Close Cloud Shell or end the session once cleanup is verified.

### Cautionary Notes

- **Always review** `terraform plan` before applying changes to avoid creating unintended resources.
- **Be careful when running** `terraform destroy` because it permanently deletes the resources managed by the configuration.
- **Save the Terraform file before running commands**; unsaved changes will not be applied.
- **Confirm you are in the correct directory** so Terraform runs against the intended configuration.
- If working in a shared Azure subscription, verify the resource group name to avoid impacting other environments.

### Tips for Efficiency

- Keep all Terraform files in a dedicated project folder such as `Terraform` for easier management.
- Reuse `terraform plan` after every configuration change to validate only the delta.
- Use clear, consistent naming for resource groups, VNets, subnets, and NSGs to simplify verification.
- Check Azure portal resources after each apply to catch issues early.
- When iterating on the lab, make small changes one at a time so troubleshooting is easier.

