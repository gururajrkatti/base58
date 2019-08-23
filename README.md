# base58

[![PyPI Version][pypi-image]](https://pypi.python.org/pypi?name=base58&:action=display)
[![PyPI Downloads][pypi-downloads-image]](https://pypi.python.org/pypi?name=base58&:action=display)
[![Build Status][travis-image]](https://travis-ci.org/keis/base58)
[![Coverage Status][coveralls-image]](https://coveralls.io/r/keis/base58?branch=master)

Base58 and Base58Check implementation compatible with what is used by the
bitcoin network. Any other alternative alphabet (like the Ripple one) can be used.


## Command line usage

    $ printf "hello world" | base58
    StV1DL6CwTryKyV

    $ printf "hello world" | base58 -c
    3vQB7B6MrGQZaxCuFg4oh

    $ printf "3vQB7B6MrGQZaxCuFg4oh" | base58 -dc
    hello world

    $ printf "4vQB7B6MrGQZaxCuFg4oh" | base58 -dc
    Invalid checksum


## Module usage

    >>> import base58
    >>> base58.b58encode(b'hello world')
    'StV1DL6CwTryKyV'
    >>> base58.b58decode(b'StV1DL6CwTryKyV')
    b'hello world'
    >>> base58.b58encode_check(b'hello world')
    '3vQB7B6MrGQZaxCuFg4oh'
    >>> base58.b58decode_check(b'3vQB7B6MrGQZaxCuFg4oh')
    b'hello world'
    >>> base58.b58decode_check(b'4vQB7B6MrGQZaxCuFg4oh')
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
      File "base58.py", line 89, in b58decode_check
        raise ValueError("Invalid checksum")
    ValueError: Invalid checksum
    # Use another alphabet. Here, using the built-in Ripple alphabet.
    >>> base58.b58encode(b'hello world', alphabet=base58.RIPPLE_ALPHABET)
    'StVrDLaUATiyKyV'
    >>> base58.b58decode(b'StVrDLaUATiyKyV', alphabet=base58.RIPPLE_ALPHABET)
    b'hello world'


[pypi-image]: https://img.shields.io/pypi/v/base58.svg?style=flat
[pypi-downloads-image]: https://img.shields.io/pypi/dm/base58.svg?style=flat
[travis-image]: https://img.shields.io/travis/keis/base58.svg?style=flat
[coveralls-image]: https://img.shields.io/coveralls/keis/base58.svg?style=flat
