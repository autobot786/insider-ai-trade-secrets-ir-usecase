# Synthetic Data Dictionary

All files are **synthetic** and intended for analysis practice.

## docs_audit.csv
- timestamp (ISO)
- user
- action: view/download/export
- space: doc/wiki space
- object_id
- data_sensitivity: internal/restricted/crown_jewel
- bytes
- device
- ip (internal)

## git_audit.csv
- timestamp
- user
- action: git_fetch/git_pull/git_clone/git_clone_mirror/git_bundle_create/git_archive_download
- repo
- repo_sensitivity
- bytes_out
- device
- ip

## id_auth.csv
- timestamp
- user
- event: login_success/mfa_challenge
- src_ip (public)
- src_country
- vpn_used
- vpn_exit_country
- asn
- device
- auth_method

## proxy.csv
- timestamp
- user
- device
- dest_domain
- dest_category
- http_method
- bytes_out
- process_name
- user_agent

## dlp.csv
- timestamp
- user
- action: upload_allowed/upload_blocked
- destination_category
- destination
- file_name
- file_size
- data_sensitivity
- policy
- device

## edr.csv
- timestamp
- user
- device
- event_type: process_start/file_create/file_delete
- process_name
- command_line
- file_path
- file_size
- data_sensitivity

## travel_records.csv
- date (YYYY-MM-DD)
- user
- travel_country
- source
