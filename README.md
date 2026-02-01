The [learn-c3.org](https://learn-c3.org) website source code.

## Contributing
If you have any suggestions for what could be added or changed, feel free
to open an issue or PR.

This website is built with Hugo. You can run it locally with `hugo server`
or with docker using: 

```
docker run --rm -it -v "$(pwd)":/project -p 1313:1313 ghcr.io/gohugoio/hugo:latest server --bind 0.0.0.0
```

