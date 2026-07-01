# Public Detection Rules and Research

This repository is my public detection engineering workspace. It includes rules I have authored or contributed to across various formats, plus research notes and detection ideas for other telemetry.

## Detection ideas

- [Claude Code OpenTelemetry Detection Ideas](ideas/otel-claude-code/otel-claude-code.md)

## [Sigma rules](https://github.com/SigmaHQ/sigma)

- [New Agent Skills Installation Attempt Via Node.EXE](sigma/proc_creation_win_node_new_agent_skills_installed.yml)
- [Azure Sign-In With Axios User Agent](sigma/azure_ad_signin_axios_user_agent.yml)
- [FortiGate - Firewall Address Object Added](sigma/fortinet_fortigate_new_firewall_address_object.yml)
- [FortiGate - New Administrator Account Created](sigma/fortinet_fortigate_new_admin_account_created.yml)
- [FortiGate - New Firewall Policy Added](sigma/fortinet_fortigate_new_firewall_policy_added.yml)
- [FortiGate - New Local User Created](sigma/fortinet_fortigate_new_local_user_created.yml)
- [FortiGate - New VPN SSL Web Portal Added](sigma/fortinet_fortigate_new_vpn_ssl_web_portal.yml)
- [FortiGate - User Group Modified](sigma/fortinet_fortigate_user_group_modified.yml)
- [FortiGate - VPN SSL Settings Modified](sigma/fortinet_fortigate_vpn_ssl_settings_modified.yml)
- [Inbox Rules Creation Or Update Activity in O365](sigma/microsoft365_susp_inbox_rule_creation_or_update_activity.yml)
- [Inbox Rules Creation Or Update Activity Via ExchangePowerShell Cmdlet](sigma/posh_ps_inbox_rule_creation_or_update_activity.yml)
- [Mail Forwarding/Redirecting Activity Via ExchangePowerShell Cmdlet](sigma/posh_ps_email_forwarding_activity.yml)
- [OpenCanary - Host Port Scan (SYN Scan)](sigma/opencanary_portscan_syn_scan.yml)
- [OpenCanary - NMAP FIN Scan](sigma/opencanary_portscan_nmap_fin_scan.yml)
- [OpenCanary - NMAP NULL Scan](sigma/opencanary_portscan_nmap_null_scan.yml)
- [OpenCanary - NMAP OS Scan](sigma/opencanary_portscan_nmap_os_scan.yml)
- [OpenCanary - NMAP XMAS Scan](sigma/opencanary_portscan_nmap_xmas_scan.yml)
- [OpenCanary - RDP New Connection Attempt](sigma/opencanary_rdp_connection_attempt.yml)
- [RedTail Cryptominer User-Agent](sigma/web_malware_redtail_useragent.yml)
- [Suspicious Email Delivered In Microsoft 365](sigma/microsoft365_suspicious_email_delivered.yml)
- [System Language Discovery via Reg.Exe](sigma/proc_creation_win_reg_system_language_discovery.yml)

## [Nova rules](https://github.com/Nova-Hunting/nova-rules)

- [Claude Conversation Enders](nova/claude_conversation_enders.nov)
- [Claude Refusal Magic String](nova/claude_magic_string.nov)
- [Honeypot Rules](nova/honeypot.nov)
- [Inject Dynamic Context](nova/inject_dynamic_context.nov)
- [Skill Rules](nova/skill_rules.nov)
- [Hidden Unicode](nova/hidden_unicode.nov)

## [Elastic rules](https://github.com/elastic/detection-rules)

- [M365 Exchange Inbox Forwarding Rule Created](elastic/collection_exchange_new_inbox_rule.toml)
- [M365 Exchange Inbox Phishing Evasion Rule Created](elastic/defense_evasion_exchange_new_inbox_rule_delete_or_move.toml)
