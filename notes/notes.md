# notes

## Dev on macOS

* building failed

Resolved 8 packages in 6ms
  × Failed to build `mysqlclient==2.2.0`
  ├─▶ The build backend returned an error
  ╰─▶ Call to `setuptools.build_meta.build_wheel` failed (exit status: 1)

```shell
brew install pkg-config
```

```shell
$ uv sync                
warning: The `requires-python` specifier (`~=3.10`) in `main` uses the tilde specifier (`~=`) without a patch version. This will be interpreted as `>=3.10, <4`. Did you mean `~=3.10.0` to constrain the version as `>=3.10.0, <3.11`? We recommend only using the tilde specifier with a patch version to avoid ambiguity.
Resolved 8 packages in 15ms
      Built main @ file:///Users/hong/repos/image_board
  × Failed to build `mysqlclient==2.2.0`
  ├─▶ The build backend returned an error
  ╰─▶ Call to `setuptools.build_meta.build_wheel` failed (exit status: 1)

      [stdout]
      Trying pkg-config --exists mysqlclient
      Command 'pkg-config --exists mysqlclient' returned non-zero exit status 1.
      Trying pkg-config --exists mariadb
      Command 'pkg-config --exists mariadb' returned non-zero exit status 1.

      [stderr]
      Traceback (most recent call last):
        File "<string>", line 14, in <module>
        File "/Users/hong/.cache/uv/builds-v0/.tmpOSLa4H/lib/python3.10/site-packages/setuptools/build_meta.py", line 333, in
      get_requires_for_build_wheel
          return self._get_build_requires(config_settings, requirements=[])
        File "/Users/hong/.cache/uv/builds-v0/.tmpOSLa4H/lib/python3.10/site-packages/setuptools/build_meta.py", line 301, in
      _get_build_requires
          self.run_setup()
        File "/Users/hong/.cache/uv/builds-v0/.tmpOSLa4H/lib/python3.10/site-packages/setuptools/build_meta.py", line 317, in
      run_setup
          exec(code, locals())
        File "<string>", line 154, in <module>
        File "<string>", line 48, in get_config_posix
        File "<string>", line 27, in find_package_name
      Exception: Can not find valid pkg-config name.
      Specify MYSQLCLIENT_CFLAGS and MYSQLCLIENT_LDFLAGS env vars manually

      hint: This usually indicates a problem with the package or the build environment.
  help: `mysqlclient` (v2.2.0) was included because `main` (v0.1.0) depends on `mysqlclient`
```

* Tips from [pypi.org/project/mysqlclient](https://pypi.org/project/mysqlclient/)
* If you don't want to install MySQL server, you can use mysql-client instead:

```shell
$ # Assume you are activating Python 3 venv
$ brew install mysql-client pkg-config
$ export PKG_CONFIG_PATH="$(brew --prefix)/opt/mysql-client/lib/pkgconfig"
$ uv sync
```