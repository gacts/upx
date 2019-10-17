<p align="center">
  <img src="https://avatars0.githubusercontent.com/u/44036562?s=200&v=4" alt="Logo" width="128" />
</p>

![Release version][badge_release_version]
[![Docker Build][badge_docker_build]][link_docker_hub]
[![Build Status][badge_build]][link_build]
[![License][badge_license]][link_license]

This is a GitHub Action to run [UPX][link_upx] on an executable file(s).

> Action idea looked in [joshuarli/strip-upx-action](https://github.com/joshuarli/strip-upx-action)

## Usage

Pack single file:

```yaml
steps:
- name: compile test file
  run: |
    printf %s 'package main;import "fmt";func main(){fmt.Println("hi")}' > main.go
    go build -o hi main.go

- uses: actions-github/upx@master
  with:
    file: 'hi'
    upx_args: '-9'

# Or use ready docker image:

- uses: docker://gact/upx:latest
  with:
    file: 'hi'
    upx_args: '-9'
```

or a directory with executable files:

```yaml
steps:
- name: compile test file
  run: |
    printf %s 'package main;import "fmt";func main(){fmt.Println("hi")}' > main.go
    go build -o hi main.go

- uses: actions-github/upx@master
  with:
    dir: '.'
    upx_args: '-9'

# Or use ready docker image:

- uses: docker://gact/upx:latest
  with:
    dir: '.'
    upx_args: '-9'
```

## Support

[![Issues][badge_issues]][link_issues]
[![Issues][badge_pulls]][link_pulls]

If you will find any package errors, please, [make an issue][link_create_issue] in current repository.

## License

This is open-sourced software licensed under the [WTFPL License][link_license].

[badge_build]:https://github.com/actions-github/upx/workflows/Test%20action/badge.svg
[badge_docker_build]:https://img.shields.io/docker/cloud/build/gact/upx.svg?maxAge=30
[badge_release_version]:https://img.shields.io/github/release/actions-github/upx.svg?maxAge=30
[badge_license]:https://img.shields.io/github/license/actions-github/upx.svg?longCache=true
[badge_issues]:https://img.shields.io/github/issues/actions-github/upx.svg?maxAge=45
[badge_pulls]:https://img.shields.io/github/issues-pr/actions-github/upx.svg?maxAge=45

[link_build]:https://github.com/actions-github/upx/actions
[link_license]:https://github.com/actions-github/upx/blob/master/LICENSE
[link_issues]:https://github.com/actions-github/upx/issues
[link_create_issue]:https://github.com/actions-github/upx/issues/new
[link_pulls]:https://github.com/actions-github/upx/pulls
[link_docker_hub]:https://hub.docker.com/r/gact/upx

[link_upx]:https://github.com/upx/upx
