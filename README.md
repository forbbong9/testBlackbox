#### Blackbox commands

| Name: | Description:  |
|-------------------------------------|-------------------------------------------------------------------------|
| `blackbox_edit <file>`  | Decrypt, run $EDITOR, re-encrypt a file |
| `blackbox_edit_start <file>`  | Decrypt a file so it can be updated |
| `blackbox_edit_end <file>`  | Encrypt a file after blackbox_edit_start was used |
| `blackbox_cat <file>` | Decrypt and view the contents of a file |
| `blackbox_view <file>`  | Like blackbox_cat but pipes to `less` or $PAGER |
| `blackbox_diff` | Diff decrypted files against their original crypted version |
| `blackbox_initialize` | Enable blackbox for a GIT or HG repo  |
| `blackbox_register_new_file <file>` | Encrypt a file for the first time |
| `blackbox_deregister_file <file>` | Remove a file from blackbox |
| `blackbox_list_files` | List the files maintained by blackbox |
| `blackbox_list_admins`  | List admins currently authorized for blackbox |
| `blackbox_decrypt_file <file>`  | Decrypt a file  |
| `blackbox_decrypt_all_files`  | Decrypt all managed files (INTERACTIVE) |
| `blackbox_postdeploy` | Decrypt all managed files (batch) |
| `blackbox_addadmin <gpg-key>` | Add someone to the list of people that can encrypt/decrypt secrets  |
| `blackbox_removeadmin <gpg-key>`  | Remove someone from the list of people that can encrypt/decrypt secrets |
| `blackbox_shred_all_files`  | Safely delete any decrypted files |
| `blackbox_update_all_files` | Decrypt then re-encrypt all files. Useful after keys are changed  |
| `blackbox_whatsnew <file>`  | show what has changed in the last commit for a given file |


#### How it works:
1. Generate a new GPG key `gpg --full-generate-key`. 
Or exporting your GPG key `gpg --armor --export _you@example.com_ > mykey.asc`.
2. To add someone else's public key, run `gpg --import theirkey.asc`.
3. `blackbox_initialize` inside the repo.
4. To encrypt a new file, run `blackbox_register_new_file`.
5. To add an admin, run `blackbox_addadmin`.
6. If just add a new admin, run `blackbox_update_all_files`.
7. To read a file, run `blackbox_cat filename`.
8. To edit a file, run `blackbox_edit filename`.


**Best reference: [blackbox GitHub page](https://github.com/StackExchange/blackbox/blob/master/README.md)**
