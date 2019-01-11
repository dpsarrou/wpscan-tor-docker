# Wpscan with Tor proxy

Easily run Wpscan with Tor proxy in docker. This project uses the default wpscan docker image and a lightweight alpine image for Tor proxy.

Use this tool **only** for WordPress websites you own, to assess the security of them and plan accordingly.

## Usage

For convience use the simple bash script wrapper `./wpscan` to run the tool. The script just wraps docker commands.

To see all available options:
```
./wpscan --help
```

### Simplest example
```
./wpscan --url http://example.com
```

Note: the first time you run the tool, it will take some time since it will pull the wpscan image and build the tor image.

## Updating

Updating is simply done by pulling the latest image.

```
docker pull wpscanteam/wpscan
```

## Configuration

The project has been setup to work out of the box with Tor proxy. In case you want
to add more configuration options you can edit:

- `cli_options.yml` For Wpscan configuration
- `tor/torrc` For Tor configuration

## Wpscan password lists

Due to the nature of containers, if you want to use files from a tool that runs in a container,
you need to share the files in the container itself. This setup automatically shares
the `passwordlists` directory and  maps it to `/wpscan/passwordlists` in the container.
If you drop a password list file to this folder it will be available for use with the tool.

#### Example

Assuming you have copied the popular `rockyou.txt` list in the `passwordlists` folder,
you can use it with:

```
./wpscan -P /wpscan/passwordlists/rockyou.txt --url http://example.com  <...extra options/arguments here if needed...>
```

Note that you need to use the **full path** as it is mapped in the container.