# Proof of Concept

this demonstrates `nargo export` ignoring namespacing and overwriting export fn
collisions

## Reproduce

both [`lib`](src/lib.nr) and [`other`](src/other.nr) contain an exported fn
`thing() -> Field`; one returns `1`, the other returns `2`, to ensure differing
bytecode

comment out each one individually and run `nargo export` each time. results are
below in the `bytecode` field of the json export

## Results

only `thing` in `src/lib.nr`

```
H4sIAAAAAAAA/6XOMQ6AMAwDwPZHSZO0zsZXqEj//wSWIpBALL3FkgfLOd1yeru6bSat4eeWUFWNVoKFdyreYaTWKxhssKNAJKBo3r2Rs0rwMJcxx9LP3y8nkUof0+wAAAA=
```

only `thing` in `src/other.nr`

```

H4sIAAAAAAAA/6XOMQ6AMAwDwPZHSZO0zsZXqEj//wQGQCCBWHqLJQ+Wc7rl9HZ1y5k0h59bQlU1WgkWXql4h5Far2CwwbYCkYCiefdGzirBw1xiHNLP3y87LSE/W+wAAAA=
```

both `thing` in `src/lib.nr` and `src/other.nr` (same as only `src/other.nr`)

```
H4sIAAAAAAAA/6XOMQ6AMAwDwPZHSZO0zsZXqEj//wQGQCCBWHqLJQ+Wc7rl9HZ1y5k0h59bQlU1WgkWXql4h5Far2CwwbYCkYCiefdGzirBw1xiHNLP3y87LSE/W+wAAAA=
```


