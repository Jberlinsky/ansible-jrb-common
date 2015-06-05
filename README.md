# ansible-jrb-common

## What it does

Some common tasks used when deploying Ubuntu servers to EC2:

- Update apt
- Install git
- Install pip
- Install boto
- Configure boto with an AWS key and secret
- Add the host to route53 based on its name in EC2
- Install UFW
- Install `make`, et. al.
- Allow SSH via port 22; deny all other traffic to the server

Also depends on some other tasks that:

- Update apt regularly
- Set up users on the server
- Set up the sudoers file
- Set the hostname on the instance
- Install Zookeeper
- Set up remote syslogging

## Expected Variables

- `fqdn_zone`: Hosted zone to register the ELB under.
- `fqdn`: `fqdn_zone`, but with a leading `.`.
- `aws_access_key_id`: AWS access key
- `aws_secret_access_key`: AWS secret access key. This and `aws_access_key` should be set via `ansible-vault`

## Dependencies

`ansible-jrb-common` depends upon the following roles:

- `ansible-cron-apt`
- `ansible-users`
- `ansible-sudo`
- `ansible-fqdn`
- `ansible-zookeeper`
- `ansible-remote-syslog`

## Use

Via ansible-galaxy, add the following to your `requirements.yml` file:

`- src: https://github.com/Jberlinsky/ansible-jrb-common`

Then just depend on the `ansible-jrb-common` role in your playbook. You should probably run it before other tasks.

## License

See LICENSE.txt

## Author

Built with love by [Jason Berlinsky](http://www.jasonberlinsky.com/)
