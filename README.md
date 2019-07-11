# ansible-clone-copy-rename
Role custom de Ansible para descargar archivos desde un repo, copiarlos a diferentes directorios y renombrarlos si es necesario.

| :warning: | WARNING: este Ansible Role fue creado con fines específicos dentro de la empresa Navent y no esta pensando para un uso general. |
| --- | --- |


Requirements
------------

Ubuntu
Git
Ansible 2.6

Role Variables
--------------

```
git_repo: "https://<YOUT-GIT-USERNAME>:<YOUR-GIT-PASSWORD>@<GIT-REPO-URL>"
git_dest: "/tmp/{{git_repo|basename}}" # (OPCIONAL) directorio temporal donse se clona el repositorio Git
git_version: "master" # version del repositorio que se quiere descargar
bumex_files_dir: "/home/ubuntu/navent/app/bumex.intranet.imovelweb.prepro.xml" # directorio donde se copiaran los archivos
files_ccr:
  - 
    relative_src: "WebContent/WEB-INF/config" # archivo o directorio que se copiara (ruta relativa al directorio donde se clono el repo)
    dest: "{{bumex_files_dir}}" # directorio de destino dodne se copia el archivo o directorio
  - 
    relative_src: "WebContent/WEB-INF/databases" # archivo o directorio que se copiara (ruta relativa al directorio donde se clono el repo)
    dest: "{{bumex_files_dir}}" # directorio de destino dodne se copia el archivo o directorio
  - 
    relative_src: "WebContent/WEB-INF/bumex.RealEstate.Intranet.xml.Brasil.prepro" # archivo o directorio que se copiara (ruta relativa al directorio donde se clono el repo)
    dest: "{{bumex_files_dir}}" # directorio de destino dodne se copia el archivo o directorio
    new_name: "bumex.xml" # nombre nuevo del archivo o directorio copiado
```

Example: 
```
git_repo: "https://<YOUT-GIT-USERNAME>:<YOUR-GIT-PASSWORD>@github.com/ITNavent/bumex.git"
git_dest: "/tmp/{{git_repo|basename}}" # (OPCIONAL) directorio temporal para clonar el repositorio Git
git_version: "master" # version del repositorio que se quiere descargar
bumex_files_dir: "/home/ubuntu/navent/app/bumex.intranet.imovelweb.prepro.xml"
files_ccr:
  - 
    relative_src: "WebContent/WEB-INF/config"
    dest: "{{bumex_files_dir}}"
  - 
    relative_src: "WebContent/WEB-INF/databases"
    dest: "{{bumex_files_dir}}"
  - 
    relative_src: "WebContent/WEB-INF/bumex.RealEstate.Intranet.xml.Brasil.prepro"
    dest: "{{bumex_files_dir}}"
    new_name: "bumex.xml"
```

Example Playbook
----------------

```
    - hosts: tag_intra-crm-manager
      roles:
         - clone-copy-rename
```

Author Information
------------------

Augusto Mendoza (amendoza@navent.com)

