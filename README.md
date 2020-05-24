APU2/3 GPIO access library
==========================

# Important

The difference between this repo and [apu_gpio_lib](https://github.com/pcengines/apu_gpio_lib), I compiled the examples to use
in my *APU2C3* with pfsense (FreeBSD v12)

## Upload examples to your pfsense router

```sh
scp -r apu_gpio_lib admin@<PFSENSE_IP>:/root
cd apu_gpio_lib/build-compiled-freebsd-12/example

# Test
./blinky
./simswap
```

This is library for accessing the GPIO's of APU2/3 devices. Currently it
supports accessing the GPIO's controlling the LED1,2,3, MODESW signal and
SIMSWAP signal (apu3 only).

This library could be used as an example.

Required tools to build
-----------------------

* gcc
* cmake

How to compile
--------------

By default compiles statically linked library and some examples.

```
mkdir build
cd build
cmake ..
make
```

Example
-------

After compilation. Examples are in dir `build/example`.
* `blinky` - it blinks the LED2 and LED3 on APU.
* `simswap` - changes the simswap pin value. Usage:
    * `./simswap`   - shows current pin state
    * `./simswap 1` - sets the simswap pin value to 1
    * `./simswap 0` - sets the simswap pin value to 0

Library API
-----------

Short API summary:

* `const char *apu_gpio_version(void)` - returns library version string
* `int apu_gpio_init(void)` - initializes the library and maps the gpio space
* `int apu_gpio_get_dir(unsigned offset)` - gets gpio direction (1 - out, 0 - in)
* `int apu_gpio_set_dir(unsigned offset, unsigned direction)` - sets gpio direction (1 - out, 0 - in)
* `int apu_gpio_get_val(unsigned offset)` - gets gpio state
* `int apu_gpio_set_val(unsigned offset, unsigned value)` - sets gpio value
