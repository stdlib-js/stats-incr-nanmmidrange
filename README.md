<!--

@license Apache-2.0

Copyright (c) 2026 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# incrnanmmidrange

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Compute a moving [mid-range][mid-range] incrementally, ignoring `NaN` values.

<section class="intro">

The [**mid-range**][mid-range], or **mid-extreme**, is the arithmetic mean of maximum and minimum values. Accordingly, the [mid-range][mid-range] is the midpoint of the [range][range] and a measure of central tendency.

</section>

<!-- /.intro -->



<section class="usage">

## Usage

```javascript
import incrnanmmidrange from 'https://cdn.jsdelivr.net/gh/stdlib-js/stats-incr-nanmmidrange@deno/mod.js';
```

#### incrnanmmidrange( window )

Returns an accumulator `function` which incrementally computes a moving [mid-range][mid-range], ignoring `NaN` values. The `window` parameter defines the number of values over which to compute the moving [mid-range][mid-range].

```javascript
var accumulator = incrnanmmidrange( 3 );
```

#### accumulator( \[x] )

If provided an input value `x`, the accumulator function returns an updated [mid-range][mid-range]. If not provided an input value `x`, the accumulator function returns the current [mid-range][mid-range].

```javascript
var accumulator = incrnanmmidrange( 3 );

var mr = accumulator();
// returns null

// Fill the window...
mr = accumulator( 2.0 ); // [2.0]
// returns 2.0

mr = accumulator( 1.0 ); // [2.0, 1.0]
// returns 1.5

mr = accumulator( 3.0 ); // [2.0, 1.0, 3.0]
// returns 2.0

// Window begins sliding...
mr = accumulator( -7.0 ); // [1.0, 3.0, -7.0]
// returns -2.0

mr = accumulator( NaN ); // [1.0, 3.0, -7.0]
// returns -2.0

mr = accumulator( -5.0 ); // [3.0, -7.0, -5.0]
// returns -2.0

mr = accumulator();
// returns -2.0
```

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   Input values are **not** type checked. If non-numeric inputs are possible, you are advised to type check and handle accordingly **before** passing the value to the accumulator function.
-   As `W` values are needed to fill the window buffer, the first `W-1` returned values are calculated from smaller sample sizes. Until the window is full, each returned value is calculated from all provided values.

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```javascript
import uniform from 'https://cdn.jsdelivr.net/gh/stdlib-js/random-base-uniform@deno/mod.js';
import bernoulli from 'https://cdn.jsdelivr.net/gh/stdlib-js/random-base-bernoulli@deno/mod.js';
import incrnanmmidrange from 'https://cdn.jsdelivr.net/gh/stdlib-js/stats-incr-nanmmidrange@deno/mod.js';

var accumulator;
var v;
var i;

// Initialize an accumulator:
accumulator = incrnanmmidrange( 5 );

// For each simulated datum, update the moving mid-range...
for ( i = 0; i < 100; i++ ) {
    v = ( bernoulli( 0.8 ) < 1 ) ? NaN : uniform( 0.0, 100.0 );
    accumulator( v );
}
console.log( accumulator() );
```

</section>

<!-- /.examples -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2026. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/stats-incr-nanmmidrange.svg
[npm-url]: https://npmjs.org/package/@stdlib/stats-incr-nanmmidrange

[test-image]: https://github.com/stdlib-js/stats-incr-nanmmidrange/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/stats-incr-nanmmidrange/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/stats-incr-nanmmidrange/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/stats-incr-nanmmidrange?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/stats-incr-nanmmidrange.svg
[dependencies-url]: https://david-dm.org/stdlib-js/stats-incr-nanmmidrange/main

-->

[chat-image]: https://img.shields.io/badge/zulip-join_chat-brightgreen.svg
[chat-url]: https://stdlib.zulipchat.com

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/stats-incr-nanmmidrange/tree/deno
[deno-readme]: https://github.com/stdlib-js/stats-incr-nanmmidrange/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/stats-incr-nanmmidrange/tree/umd
[umd-readme]: https://github.com/stdlib-js/stats-incr-nanmmidrange/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/stats-incr-nanmmidrange/tree/esm
[esm-readme]: https://github.com/stdlib-js/stats-incr-nanmmidrange/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/stats-incr-nanmmidrange/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/stats-incr-nanmmidrange/main/LICENSE

[range]: https://en.wikipedia.org/wiki/Range_%28statistics%29

[mid-range]: https://en.wikipedia.org/wiki/Mid-range

<!-- <related-links> -->

<!-- </related-links> -->

</section>

<!-- /.links -->
