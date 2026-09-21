# ansible-suite.packages

Role pro instalaci a odinstalaci systémových balíčků. Používá
`ansible.builtin.package`, takže výběr konkrétního správce balíčků deleguje na
cílový operační systém.

## Použití

```yaml
- name: Manage system packages
  hosts: all
  become: true
  roles:
    - role: ansible-suite.packages
      vars:
        packages:
          - curl
          - vim
        packages_remove:
          - telnet
```

Oba seznamy jsou ve výchozím nastavení prázdné. Balíčky v `packages` se
instalují a balíčky v `packages_remove` se odstraňují. Hodnoty mohou být i
vnořené seznamy; role je před použitím zploští pomocí filtru `flatten`.
