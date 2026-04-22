# ansible-role-wordpress-sdvh

Role Ansible pour deployer WordPress avec MariaDB sur des conteneurs Linux Ubuntu/Debian et RedHat/Rocky.

## Fonctionnalites

- Installation des paquets adaptee a la famille d'OS.
- Demarrage de MariaDB en environnement conteneurise.
- Creation de la base de donnees WordPress.
- Creation de l'utilisateur SQL WordPress.
- Telechargement et deploiement de WordPress.
- Generation de `wp-config.php` avec Jinja2.
- Demarrage d'Apache2 sur Ubuntu et de HTTPD sur Rocky.
- Handlers pour redemarrer le serveur web.

## Plateformes supportees

- Ubuntu/Debian
- Rocky/RedHat

## Variables principales

```yaml
wordpress_site_name: "SDVH WordPress"
wordpress_download_url: "https://wordpress.org/latest.tar.gz"
wordpress_tmp_dir: /tmp/wordpress
wordpress_db_name: wordpress
wordpress_db_user: wordpress
wordpress_db_password: "ChangeMe123!"
wordpress_db_host: localhost
```

## Exemple de playbook

```yaml
---
- name: Deployer WordPress SDVH
  hosts: all
  become: true

  roles:
    - ansible-role-wordpress-sdvh
```

## Execution

```bash
ansible-playbook -i inventaire playbooks/ansible-role-wordpress-sdvh.yml
```

## Verification

```bash
ansible all -m shell -a "curl -I http://127.0.0.1"
ansible all -m shell -a "ss -lnt"
```

Depuis l'hote Docker :

```bash
curl http://localhost:8083
curl http://localhost:8084
curl http://localhost:8085
curl http://localhost:8086
```

## Publication Galaxy

Pousser ce role dans un depot public GitHub/GitLab, puis l'importer depuis Ansible Galaxy.

## Licence

MIT
