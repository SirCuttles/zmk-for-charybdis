# zmk-config for charybdis (4x6)

## Building Locally

Activate the ZMK virtualenv first:

```sh
source ~/.venv/zmk/bin/activate
```

Build the left half:

```sh
west build -p always -s zmk/app -b nice_nano -d build/left -- -DZephyr_DIR="$(pwd)/zephyr/share/zephyr-package/cmake" -DSHIELD=charybdis_left -DZMK_CONFIG="$(pwd)/config/charybdis"
```

Build the right half:

```sh
west build -p always -s zmk/app -b nice_nano -d build/right -- -DZephyr_DIR="$(pwd)/zephyr/share/zephyr-package/cmake" -DSHIELD=charybdis_right -DZMK_CONFIG="$(pwd)/config/charybdis"
```

If you are using a nice!nano v2, replace `nice_nano` with `nice_nano_v2` in both commands.

The `-DZephyr_DIR=...` flag pins the build to this checkout's Zephyr tree, and `ZMK_CONFIG` points at the user config directory while the custom shield stays in the `config` module.

Build outputs:

- `build/left/zephyr/zmk.uf2`
- `build/right/zephyr/zmk.uf2`
