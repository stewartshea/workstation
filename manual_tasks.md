# List all manual tasks here and potential reasons why
- MetaNetworks
    - Login wall for onboarding a new device
    - After install, modify selinux
    ```
    sudo grep 'ipsec\|policykit_auth_t\|chrony' /var/log/audit/audit.log | audit2allow -a -M my_ipsec && sudo semodule -i my_ipsec.pp
    ```