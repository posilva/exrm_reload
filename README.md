# ExrmReload [![Build Status](https://travis-ci.org/xerions/exrm_reload.svg)](https://travis-ci.org/xerions/exrm_reload)

Build new sys.config from [conform](https://github.com/bitwalker/conform) config and apply it at runtume. 
It uses `conform_schema` and `conform_config` command line flags which are set on [exrm](https://github.com/bitwalker/exrm) startup script.

## Usage

1. Add exrm_reload to your list of dependencies in mix.exs:

    ```elixir
    def deps do
        [{:exrm_reload, github: "xerions/exrm_reload"}]
    end
    ```

2. Ensure exrm_reload is started before your application:

    ```elixir
    def application do
        [applications: [:exrm_reload]]
    end
    ```

3. Run reconfiguration when you want it:

	```elixir
	> ReleaseManager.Reload.run
	```

	or you can specify application's list for reconfiguration:

	```elixir
	> ReleaseManager.Reload.run [:hello, :exd, :ecdo]
	```

It works with the releases are builded via `exrm`. You just call it by rpc from OS shell:

	$ you_application rpc Elixir.ReleaseManager.Reload run

The test application uses xerions forks of [exrm](https://github.com/xerions/exrm) and [conform](https://github.com/xerions/conform) but it can work with the original exrm version `>= 0.19.7` and conform. Just override it.
