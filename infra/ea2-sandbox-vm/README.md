# EA2 — MV sandbox + K8s (Terraform)

Módulo mínimo para **una EC2** en el **VPC por defecto**, security group con **SSH** y rango **NodePort**, y `aws_key_pair` generado a partir de la **clave pública** derivada en CI desde `EA2_SSH_PRIVATE_KEY`.

- **State:** solo en el runner de GitHub Actions (no backend remoto).
- **Destrucción:** el sandbox de credenciales caduca (~3 h); no dependemos de `terraform destroy` aquí.
- **AWS Academy:** disco raíz por defecto **8 GiB, gp2** (muchas cuentas tienen *explicit deny* sobre **gp3** o volúmenes grandes). Si aún falla `RunInstances` sobre `volume/*`, el rol del lab puede no permitir crear instancias con disco personalizado: en ese caso habría que quitar el bloque `root_block_device` y usar solo el tamaño que trae la AMI.

Ver el workflow: `.github/workflows/ea2-provision-k8s-sandbox.yaml`.
