# kube-cli

This role enables to install kube client utilities on a system:

- `kubectl`
- `helm`

## Requirements

- [ansible-shell-aliases](https://github.com/julb/ansible-shell-aliases): to create useful aliases for `kubectl`.

## Role Variables

| Name                               | Type      | Location            | Description                                                                                |
| ---------------------------------- | --------- | ------------------- | ------------------------------------------------------------------------------------------ |
| kubectl_version                    | string    | `defaults/main.yml` | The version of kubectl to install. Defaults to `1.21.0`.                                   |
| kubectl_releases_url               | string    | `defaults/main.yml` | The base URL of kubectl releases repository. Defaults to `https://dl.k8s.io/release`.      |
| kubectl_os                         | string    | `defaults/main.yml` | The OS distribution of kubectl to install. Defaults to `linux`.                            |
| kubectl_arch                       | string    | `defaults/main.yml` | The arch distribution of kubectl to install. Defaults to `amd64`.                          |
| kubectl_executable_sha256_checksum | string    | `defaults/main.yml` | The expected checksum of the kubectl executable downloaded from the website.               |
| helm_version                       | string    | `defaults/main.yml` | The version of helm to install. Defaults to `3.5.4`.                                       |
| helm_releases_url                  | string    | `defaults/main.yml` | The base URL of helm releases repository. Defaults to `https://get.helm.sh`.               |
| helm_os                            | string    | `defaults/main.yml` | The OS distribution of helm to install. Defaults to `linux`.                               |
| helm_arch                          | string    | `defaults/main.yml` | The arch distribution of helm to install. Defaults to `amd64`.                             |
| helm_executable_sha256_checksum    | string    | `defaults/main.yml` | The expected checksum of the helm executable downloaded from the website.                  |
| kubectl_executable                 | string    | `vars/main.yml`     | The local path where to install kubectl executable. Defaults to `/usr/local/sbin/kubectl`. |
| helm_executable                    | string    | `vars/main.yml`     | The local path where to install helm executable. Defaults to `/usr/local/sbin/helm`.       |
| kube_cli_shell_aliases             | aliases[] | `defaults/main.yml` | The aliases to create on the target system. See below for defaults.                        |
| kube_cli_shell_aliases_extras      | aliases[] | `defaults/main.yml` | An extra aliases object to create custom aliases. Defaults to `[]`.                        |

The `kube_cli_shell_aliases` and `kube_cli_shell_aliases_extras` are list of `aliases` objects, which are a dictionary composed of a `name` attribute for the alias name and the `command` attribute for the command to execute.

By default, the following aliases are defined in `kube_cli_shell_aliases`:

```yaml
- name: k
  command: 'kubectl'
- name: ks
  command: 'kubectl --namespace kube-system'
- name: kctx
  command: 'kubectl config use'
```

## Dependencies

No dependencies.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: servers
  roles:
    - { role: julb.kube_cli }
```

## License

MIT

## Author Information

More to find on my [Github](https://github.com/julb).

## Contributing

This project is totally open source and contributors are welcome.

When you submit a PR, please ensure that the syntax has been checked.
