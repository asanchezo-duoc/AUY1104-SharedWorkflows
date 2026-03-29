# EA2 — MV sandbox + K8s (Terraform)

Módulo mínimo para **una EC2** en el **VPC por defecto**, security group con **SSH** y rango **NodePort**, y `aws_key_pair` generado a partir de la **clave pública** derivada en CI desde `EA2_SSH_PRIVATE_KEY`.

- **State:** solo en el runner de GitHub Actions (no backend remoto).
- **Destrucción:** el sandbox de credenciales caduca (~3 h); no dependemos de `terraform destroy` aquí.

Ver el workflow: `.github/workflows/ea2-provision-k8s-sandbox.yaml`.
