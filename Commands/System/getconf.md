# `getconf` Get system Config

- The getconf command in Linux is used to retrieve system configuration values, such as system limits, filesystem limits, page-size and POSIX-related information. It is useful for checking system properties without directly accessing system files.

- `getconf -a` to list all the configs.

- `getconf PARAMETER_NAME` will provide the info fo rthat particular parameter.
```sh
dhyanesh@dhyanesh-ThinkPad-T14s-Gen-1:~$ getconf PAGE_SIZE 
4096
```

