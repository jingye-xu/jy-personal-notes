# How to set grub to remember your last selected entry
1. Edit the file /etc/default/grub
    ```
    sudo vim /etc/default/grub
    ```
2. Look for `GRUB_DEFAULT=0`, change it to `GRUB_DEFAULT=saved`
3. Add `GRUB_SAVEDEFAULT=true` to a single blank line
4. Update the changes in grub
    ```
    sudo update-grub
    ```

# How to change the timeout time
1. Edit the file /etc/default/grub
    ```
    sudo vim /etc/default/grub
    ```
2. Look for `GRUB_TIMEOUT=5`, change it to `GRUB_TIMEOUT=n`, n means the timeout you want to set to
3. Update the changes in grub
    ```
    sudo update-grub
    ```

# How to hide grub unless the user presses the Shift key
1. Edit the file /etc/default/grub
    ```
    sudo vim /etc/default/grub
    ```
2. Add `GRUB_FORCE_HIDDEN_MENU="true"` to a single blank line
3. Update the changes in grub
    ```
    sudo update-grub
    ```
# To update grub on operating systems that do not have an “update-grub” function, run this command in the terminal:
    ```
    sudo grub-mkconfig -o /boot/grub/grub.cfg
    ```
