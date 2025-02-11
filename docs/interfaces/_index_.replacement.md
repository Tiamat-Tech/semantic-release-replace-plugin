**[@google/semantic-release-replace-plugin](../README.md)**

> [Globals](../README.md) / ["index"](../modules/_index_.md) / Replacement

# Interface: Replacement

Replacement is simlar to the interface used by https://www.npmjs.com/package/replace-in-file
with the difference being the single string for `to` and `from`.

## Hierarchy

* **Replacement**

## Index

### Properties

* [allowEmptyPaths](_index_.replacement.md#allowemptypaths)
* [countMatches](_index_.replacement.md#countmatches)
* [disableGlobs](_index_.replacement.md#disableglobs)
* [dry](_index_.replacement.md#dry)
* [encoding](_index_.replacement.md#encoding)
* [files](_index_.replacement.md#files)
* [from](_index_.replacement.md#from)
* [ignore](_index_.replacement.md#ignore)
* [results](_index_.replacement.md#results)
* [to](_index_.replacement.md#to)

## Properties

### allowEmptyPaths

• `Optional` **allowEmptyPaths**: boolean

*Defined in [index.ts:83](https://github.com/google/semantic-release-replace-plugin/blob/60c4ca8/src/index.ts#L83)*

___

### countMatches

• `Optional` **countMatches**: boolean

*Defined in [index.ts:84](https://github.com/google/semantic-release-replace-plugin/blob/60c4ca8/src/index.ts#L84)*

___

### disableGlobs

• `Optional` **disableGlobs**: boolean

*Defined in [index.ts:85](https://github.com/google/semantic-release-replace-plugin/blob/60c4ca8/src/index.ts#L85)*

___

### dry

• `Optional` **dry**: boolean

*Defined in [index.ts:87](https://github.com/google/semantic-release-replace-plugin/blob/60c4ca8/src/index.ts#L87)*

___

### encoding

• `Optional` **encoding**: string

*Defined in [index.ts:86](https://github.com/google/semantic-release-replace-plugin/blob/60c4ca8/src/index.ts#L86)*

___

### files

•  **files**: string[]

*Defined in [index.ts:38](https://github.com/google/semantic-release-replace-plugin/blob/60c4ca8/src/index.ts#L38)*

files to search for replacements

___

### from

•  **from**: From \| From[]

*Defined in [index.ts:54](https://github.com/google/semantic-release-replace-plugin/blob/60c4ca8/src/index.ts#L54)*

The RegExp pattern to use to match.

Uses `String.replace(new RegExp(s, 'gm'), to)` for implementation, if
`from` is a string.

For advanced matching, i.e. when using a `release.config.js` file, consult
the documentation of the `replace-in-file` package
(https://github.com/adamreisnz/replace-in-file/blob/main/README.md) on its
`from` option. This allows explicit specification of `RegExp`s, callback
functions, etc.

Multiple matchers may be provided as an array, following the same
conversion rules as mentioned above.

___

### ignore

• `Optional` **ignore**: string[]

*Defined in [index.ts:82](https://github.com/google/semantic-release-replace-plugin/blob/60c4ca8/src/index.ts#L82)*

___

### results

• `Optional` **results**: { file: string ; hasChanged: boolean ; numMatches?: number ; numReplacements?: number  }[]

*Defined in [index.ts:92](https://github.com/google/semantic-release-replace-plugin/blob/60c4ca8/src/index.ts#L92)*

The results array can be passed to ensure that the expected replacements
have been made, and if not, throw and exception with the diff.

___

### to

•  **to**: To \| To[]

*Defined in [index.ts:81](https://github.com/google/semantic-release-replace-plugin/blob/60c4ca8/src/index.ts#L81)*

The replacement value using a template of variables.

`__VERSION__ = "${nextRelease.version}"`

The context object is used to render the template. Additional values
can be found at: https://semantic-release.gitbook.io/semantic-release/developer-guide/js-api#result

For advanced replacement (NOTE: only for use with `release.config.js` file version), pass in a function to replace non-standard variables
```
{
   from: `__VERSION__ = 11`, // eslint-disable-line
   to: (matched) => `__VERSION: ${parseInt(matched.split('=')[1].trim()) + 1}`, // eslint-disable-line
 },
```

The `args` for a callback function can take a variety of shapes. In its
simplest form, e.g. if `from` is a string, it's the filename in which the
replacement is done. If `from` is a regular expression the `args` of the
callback include captures, the offset of the matched string, the matched
string, etc. See the `String.replace` documentation for details

Multiple replacements may be specified as an array. These can be either
strings or callback functions. Note that the amount of replacements needs
to match the amount of `from` matchers.
