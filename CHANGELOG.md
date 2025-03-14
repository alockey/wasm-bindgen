# `wasm-bindgen` Change Log
--------------------------------------------------------------------------------

## Unreleased

### Added

* Add support for multi-threading in Node.js.
  [#4318](https://github.com/rustwasm/wasm-bindgen/pull/4318)

### Changed

* Add clear error message to communicate new feature resolver version requirements.
  [#4312](https://github.com/rustwasm/wasm-bindgen/pull/4312)

### Fixed

* Fix macro-hygiene for calls to `std::thread_local!`.
  [#4315](https://github.com/rustwasm/wasm-bindgen/pull/4315)

--------------------------------------------------------------------------------

## [0.2.97](https://github.com/rustwasm/wasm-bindgen/compare/0.2.96...0.2.97)

Released 2024-11-30

### Fixed

* Fixed `js-sys` and `wasm-bindgen-futures` relying on internal paths of `wasm-bindgen` that are not crate feature additive.
  [#4305](https://github.com/rustwasm/wasm-bindgen/pull/4305)

--------------------------------------------------------------------------------

## [0.2.96](https://github.com/rustwasm/wasm-bindgen/compare/0.2.95...0.2.96)

Released 2024-11-29

### Added

* Added support for the [`HTMLOrSVGElement`](https://html.spec.whatwg.org/#htmlorsvgelement) `mixin`, which is used for all interfaces deriving from `Element`.
  [#4143](https://github.com/rustwasm/wasm-bindgen/pull/4143)

* Added bindings for [MathMLElement](https://www.w3.org/TR/MathML3).
  [#4143](https://github.com/rustwasm/wasm-bindgen/pull/4143)

* Added JSDoc type annotations to C-style enums.
  [#4192](https://github.com/rustwasm/wasm-bindgen/pull/4192)

* Added support for C-style enums with negative discriminants.
  [#4204](https://github.com/rustwasm/wasm-bindgen/pull/4204)

* Added bindings for `MediaStreamTrack.getCapabilities`.
  [#4236](https://github.com/rustwasm/wasm-bindgen/pull/4236)

* Added WASM ABI support for `u128` and `i128`
  [#4222](https://github.com/rustwasm/wasm-bindgen/pull/4222)

* Added support for the `wasm32v1-none` target.
  [#4277](https://github.com/rustwasm/wasm-bindgen/pull/4277)

* Added support for `no_std` to `js-sys`, `web-sys`, `wasm-bindgen-futures` and `wasm-bindgen-test`.
  [#4277](https://github.com/rustwasm/wasm-bindgen/pull/4277)

* Added support for `no_std` to `link_to!`, `static_string` (via `thread_local_v2`) and `throw`.
  [#4277](https://github.com/rustwasm/wasm-bindgen/pull/4277)

* Added environment variables to configure tests: `WASM_BINDGEN_USE_BROWSER`, `WASM_BINDGEN_USE_DEDICATED_WORKER`, `WASM_BINDGEN_USE_SHARED_WORKER` `WASM_BINDGEN_USE_SERVICE_WORKER`, `WASM_BINDGEN_USE_DENO` and `WASM_BINDGEN_USE_NODE_EXPERIMENTAL`. The use of `wasm_bindgen_test_configure!` will overwrite any environment variable.
  [#4295](https://github.com/rustwasm/wasm-bindgen/pull/4295)

### Changed

* String enums now generate private TypeScript types but only if used.
  [#4174](https://github.com/rustwasm/wasm-bindgen/pull/4174)

* Remove unnecessary JSDoc type annotations from generated `.d.ts` files
  [#4187](https://github.com/rustwasm/wasm-bindgen/pull/4187)

* Deprecate `autofocus`, `tabIndex`, `focus()` and `blur()` bindings in favor of bindings on the inherited `Element` class.
  [#4143](https://github.com/rustwasm/wasm-bindgen/pull/4143)

* Optimized ABI performance for `Option<{i32,u32,isize,usize,f32,*const T,*mut T}>`.
  [#4183](https://github.com/rustwasm/wasm-bindgen/pull/4183)

* Deprecate `--reference-types` in favor of automatic target feature detection.
  [#4237](https://github.com/rustwasm/wasm-bindgen/pull/4237)

* `wasm-bindgen-test-runner` now tries to restart the WebDriver on failure, instead of spending its timeout period trying to connect to a non-existing WebDriver.
  [#4267](https://github.com/rustwasm/wasm-bindgen/pull/4267)

* Deprecated `#[wasm_bindgen(thread_local)]` in favor of `#[wasm_bindgen(thread_local_v2)]`, which creates a `wasm_bindgen::JsThreadLocal`. It is similar to `std::thread::LocalKey` but supports `no_std`.
  [#4277](https://github.com/rustwasm/wasm-bindgen/pull/4277)

* Updated the WebGPU API to the current draft as of 2024-11-22.
  [#4290](https://github.com/rustwasm/wasm-bindgen/pull/4290)

* Improved error messages for `self` arguments in invalid positions.
  [#4276](https://github.com/rustwasm/wasm-bindgen/pull/4276)

### Fixed

* Fixed methods with `self: &Self` consuming the object.
  [#4178](https://github.com/rustwasm/wasm-bindgen/pull/4178)

* Fixed unused string enums generating JS values.
  [#4193](https://github.com/rustwasm/wasm-bindgen/pull/4193)

* Fixed triggering lints in testing facilities.
  [#4195](https://github.com/rustwasm/wasm-bindgen/pull/4195)

* Fixed `#[should_panic]` not working with `#[wasm_bindgen_test(unsupported = ...)]`.
  [#4196](https://github.com/rustwasm/wasm-bindgen/pull/4196)

* Fixed potential `null` error when using `JsValue::as_debug_string()`.
  [#4192](https://github.com/rustwasm/wasm-bindgen/pull/4192)

* Fixed generated types when the getter and setter of a property have different types.
  [#4202](https://github.com/rustwasm/wasm-bindgen/pull/4202)

* Fixed generated types when a static getter/setter has the same name as an instance getter/setter.
  [#4202](https://github.com/rustwasm/wasm-bindgen/pull/4202)

* Fixed invalid TypeScript return types for multivalue signatures.
  [#4210](https://github.com/rustwasm/wasm-bindgen/pull/4210)

* Only emit `table.fill` instructions if the bulk-memory proposal is enabled.
  [#4237](https://github.com/rustwasm/wasm-bindgen/pull/4237)

* Fixed calls to `JsCast::instanceof()` not respecting JavaScript namespaces.
  [#4241](https://github.com/rustwasm/wasm-bindgen/pull/4241)

* Fixed imports for functions using `this` and late binding.
  [#4225](https://github.com/rustwasm/wasm-bindgen/pull/4225)

* Don't expose non-functioning implicit constructors to classes when none are provided.
  [#4282](https://github.com/rustwasm/wasm-bindgen/pull/4282)

--------------------------------------------------------------------------------

## [0.2.95](https://github.com/rustwasm/wasm-bindgen/compare/0.2.94...0.2.95)

Released 2024-10-10

### Added

* Added support for implicit discriminants in enums.
  [#4152](https://github.com/rustwasm/wasm-bindgen/pull/4152)

* Added support for `Self` in complex type expressions in methods.
  [#4155](https://github.com/rustwasm/wasm-bindgen/pull/4155)

### Changed

* String enums are no longer generate TypeScript types.
  [#4174](https://github.com/rustwasm/wasm-bindgen/pull/4174)

### Fixed

* Fixed generated setters from WebIDL interface attributes binding to wrong JS method names.
  [#4170](https://github.com/rustwasm/wasm-bindgen/pull/4170)

* Fix string enums showing up in JS documentation and TypeScript bindings without corresponding types.
  [#4175](https://github.com/rustwasm/wasm-bindgen/pull/4175)

--------------------------------------------------------------------------------

## [0.2.94](https://github.com/rustwasm/wasm-bindgen/compare/0.2.93...0.2.94) (YANKED)

Released 2024-10-09

### Added

* Added support for the WebAssembly `Tail Call` proposal.
  [#4111](https://github.com/rustwasm/wasm-bindgen/pull/4111)

* Add bindings for `RTCPeerConnection.setConfiguration(RTCConfiguration)` method.
  [#4105](https://github.com/rustwasm/wasm-bindgen/pull/4105)

* Add bindings to `RTCRtpTransceiverDirection.stopped`.
  [#4102](https://github.com/rustwasm/wasm-bindgen/pull/4102)

* Added experimental support for `Symbol.dispose` via `WASM_BINDGEN_EXPERIMENTAL_SYMBOL_DISPOSE`.
  [#4118](https://github.com/rustwasm/wasm-bindgen/pull/4118)

* Added bindings for the draft [WebRTC Encoded Transform](https://www.w3.org/TR/webrtc-encoded-transform) spec.
  [#4125](https://github.com/rustwasm/wasm-bindgen/pull/4125)

* Added `Debug` implementation to `JsError`.
  [#4136](https://github.com/rustwasm/wasm-bindgen/pull/4136)

* Added support for `js_name` and `skip_typescript` attributes for string enums.
  [#4147](https://github.com/rustwasm/wasm-bindgen/pull/4147)

* Added `unsupported` crate to `wasm_bindgen_test(unsupported = test)` as a way of running tests on non-Wasm targets as well.
  [#4150](https://github.com/rustwasm/wasm-bindgen/pull/4150)

* Added additional bindings for methods taking buffer view types (e.g. `&[u8]`) with corresponding JS types (e.g. `Uint8Array`).
  [#4156](https://github.com/rustwasm/wasm-bindgen/pull/4156)

* Added additional bindings for setters from WebIDL interface attributes with applicaple parameter types of just `JsValue`.
  [#4156](https://github.com/rustwasm/wasm-bindgen/pull/4156)

### Changed

* Implicitly enable reference type and multivalue transformations if the module already makes use of the corresponding target features.
  [#4133](https://github.com/rustwasm/wasm-bindgen/pull/4133)

* Updated Gamepad API.
  [#4134](https://github.com/rustwasm/wasm-bindgen/pull/4134)

* Deprecated `Gamepad::display_id` and `GamepadHapticActuator::type_`.
  [#4134](https://github.com/rustwasm/wasm-bindgen/pull/4134)

* Removed `GamepadAxisMoveEvent`, `GamepadAxisMoveEventInit`, `GamepadButtonEvent`, `GamepadButtonEventInit` and `GamepadServiceTest`, which were seemingly never implemented by any JS environment.
  [#4134](https://github.com/rustwasm/wasm-bindgen/pull/4134)

* Changed `TextDecoder.decode()` `input` parameter type from `&mut [u8]` to `&[u8]`.
  [#4141](https://github.com/rustwasm/wasm-bindgen/pull/4141)

* Updated the WebGPU API to the current draft as of 2024-10-07.
  [#4145](https://github.com/rustwasm/wasm-bindgen/pull/4145)

* Deprecated generated setters from WebIDL interface attribute taking `JsValue` in favor of newer bindings with specific parameter types.
  [#4156](https://github.com/rustwasm/wasm-bindgen/pull/4156)

### Fixed

* Fixed linked modules emitting snippet files when not using `--split-linked-modules`.
  [#4066](https://github.com/rustwasm/wasm-bindgen/pull/4066)

* Fixed incorrect deprecation warning when passing no parameter into `default()` (`init()`) or `initSync()`.
  [#4074](https://github.com/rustwasm/wasm-bindgen/pull/4074)

* Fixed many proc-macro generated `impl` blocks missing `#[automatically_derived]`, affecting test coverage.
  [#4078](https://github.com/rustwasm/wasm-bindgen/pull/4078)

* Fixed negative `BigInt` values being incorrectly formatted with two minus signs.
  [#4082](https://github.com/rustwasm/wasm-bindgen/pull/4082)
  [#4088](https://github.com/rustwasm/wasm-bindgen/pull/4088)

* Fixed emitted `package.json` structure to correctly specify its dependencies
  [#4091](https://github.com/rustwasm/wasm-bindgen/pull/4091)

* Fixed returning `Option<Enum>` now correctly has the `| undefined` type in TS bindings.
  [#4137](https://github.com/rustwasm/wasm-bindgen/pull/4137)

* Fixed enum variant name collisions with object prototype fields.
  [#4137](https://github.com/rustwasm/wasm-bindgen/pull/4137)

* Fixed multiline doc comment alignment and remove empty ones entirely.
  [#4135](https://github.com/rustwasm/wasm-bindgen/pull/4135)

* Fixed `experimental-nodejs-module` target when used with `#[wasm_bindgen(start)]`.
  [#4093](https://github.com/rustwasm/wasm-bindgen/pull/4093)

* Fixed error when importing very large JS files.
  [#4146](https://github.com/rustwasm/wasm-bindgen/pull/4146)

* Specify `"type": "module"` when deploying to nodejs-module
  [#4092](https://github.com/rustwasm/wasm-bindgen/pull/4092)

* Fixed string enums not generating TypeScript types.
  [#4147](https://github.com/rustwasm/wasm-bindgen/pull/4147)

* Bindings that take buffer view types (e.g. `&[u8]`) as parameters will now correctly return a `Result` when they might not support a backing `SharedArrayBuffer`. This only applies to new and unstable APIs, which won't cause a breaking in the API.
  [#4156](https://github.com/rustwasm/wasm-bindgen/pull/4156)

--------------------------------------------------------------------------------

## [0.2.93](https://github.com/rustwasm/wasm-bindgen/compare/0.2.92...0.2.93)

Released 2024-08-13

### Added

* Allow exporting functions named `default`. Throw error in wasm-bindgen-cli if --target web and
  an exported symbol is named `default`.
  [#3930](https://github.com/rustwasm/wasm-bindgen/pull/3930)

* Added support for arbitrary expressions when using `#[wasm_bindgen(typescript_custom_section)]`.
  [#3901](https://github.com/rustwasm/wasm-bindgen/pull/3901)

* Implement `From<NonNull<T>>` for `JsValue`.
  [#3877](https://github.com/rustwasm/wasm-bindgen/pull/3877)

* Add method `copy_within` for TypedArray, add methods `find_last`,`find_last_index` for Array.
  [#3888](https://github.com/rustwasm/wasm-bindgen/pull/3888)

* Added support for returning `Vec`s from async functions.
  [#3630](https://github.com/rustwasm/wasm-bindgen/pull/3630)

* Added bindings for `InputDeviceInfo` and `MediaTrackCapabilities`.
  [#3935](https://github.com/rustwasm/wasm-bindgen/pull/3935)

* Add bindings for `RTCRtpReceiver.getCapabilities(DOMString)` method.
  [#3941](https://github.com/rustwasm/wasm-bindgen/pull/3941)

* Add bindings for `VisualViewport`.
  [#3931](https://github.com/rustwasm/wasm-bindgen/pull/3931)

* Add bindings for `queueMicrotask`.
  [#3981](https://github.com/rustwasm/wasm-bindgen/pull/3981)

* Add experimental bindings for User Agent Client Hints API
  [#3989](https://github.com/rustwasm/wasm-bindgen/pull/3989)

* Add bindings for `FocusOptions`.
  [#3996](https://github.com/rustwasm/wasm-bindgen/pull/3996)

* Add bindings for `RTCRtpReceiver.jitterBufferTarget`.
  [#3968](https://github.com/rustwasm/wasm-bindgen/pull/3968)

* Generate getters for all WebIDL dictionary types.
  [#3993](https://github.com/rustwasm/wasm-bindgen/pull/3993)

* Support for iterable in WebIDL. Gives `entries`, `keys`, `values` methods for regular and asynchronous, as well as `for_each` for regular, iterables.
  [#3962](https://github.com/rustwasm/wasm-bindgen/pull/3962)

* Add bindings for `HTMLTableCellElement.abbr` and `scope` properties.
  [#3972](https://github.com/rustwasm/wasm-bindgen/pull/3972)

* Add WebIDL definitions relating to `Popover API`.
  [#3977](https://github.com/rustwasm/wasm-bindgen/pull/3977)

* Added the `thread_stack_size` property to the object parameter of `default()` (`init()`) and `initSync()`, making it possible to set the stack size of spawned threads. `__wbindgen_thread_destroy()` now has a third optional parameter for the stack size, the default stack size is assumed when not passing it. When calling from the thread to be destroyed, by passing no parameters, the correct stack size is determined internally.
  [#3995](https://github.com/rustwasm/wasm-bindgen/pull/3995)

* Added bindings to the Device Memory API.
  [#4011](https://github.com/rustwasm/wasm-bindgen/pull/4011)

* Added support for WebIDL records. This added new methods to various APIs, notably `ClipboardItem()`, `GPUDeviceDescriptor.requiredLimits` and `Header()`.
  [#4030](https://github.com/rustwasm/wasm-bindgen/pull/4030)

* Added an official MSRV policy. Library MSRV changes will be accompanied by a minor version bump. CLI tool MSRV can change with any version bump.
  [#4038](https://github.com/rustwasm/wasm-bindgen/pull/4038)

* Added bindings to `NavigatorOptions.vibrate`.
  [#4041](https://github.com/rustwasm/wasm-bindgen/pull/4041)

* Added an experimental Node.JS ES module target, in comparison the current `node` target uses CommonJS, with `--target experimental-nodejs-module` or when testing with `wasm_bindgen_test_configure!(run_in_node_experimental)`.
  [#4027](https://github.com/rustwasm/wasm-bindgen/pull/4027)

* Added importing strings as `JsString` through `#[wasm_bindgen(thread_local, static_string)] static STRING: JsString = "a string literal";`.
  [#4055](https://github.com/rustwasm/wasm-bindgen/pull/4055)

* Added experimental test coverage support for `wasm-bindgen-test-runner`, see the guide for more information.
  [#4060](https://github.com/rustwasm/wasm-bindgen/pull/4060)

### Changed

* Stabilize Web Share API.
  [#3882](https://github.com/rustwasm/wasm-bindgen/pull/3882)

* Generate JS bindings for WebIDL dictionary setters instead of using `Reflect`. This increases the size of the Web API bindings but should be more performant. Also, importing getters/setters from JS now supports specifying the JS attribute name as a string, e.g. `#[wasm_bindgen(method, setter = "x-cdm-codecs")]`.
  [#3898](https://github.com/rustwasm/wasm-bindgen/pull/3898)

* Greatly improve the performance of sending WebIDL 'string enums' across the JavaScript boundary by converting the enum variant string to/from an int.
  [#3915](https://github.com/rustwasm/wasm-bindgen/pull/3915)

* Use `table.fill` when appropriate.
  [#3446](https://github.com/rustwasm/wasm-bindgen/pull/3446)

* Annotated methods in WebCodecs that throw.
  [#3970](https://github.com/rustwasm/wasm-bindgen/pull/3970)

* Update and stabilize the Clipboard API.
  [#3992](https://github.com/rustwasm/wasm-bindgen/pull/3992)

* Deprecate builder-pattern type setters for WebIDL dictionary types and introduce non-mutable setters instead.
  [#3993](https://github.com/rustwasm/wasm-bindgen/pull/3993)

* Allow imported async functions to return any type that can be converted from a `JsValue`.
  [#3919](https://github.com/rustwasm/wasm-bindgen/pull/3919)

* Update Web Authentication API to level 3.
  [#4000](https://github.com/rustwasm/wasm-bindgen/pull/4000)

* Deprecate `AudioBufferSourceNode.onended` and `AudioBufferSourceNode.stop()`.
  [#4020](https://github.com/rustwasm/wasm-bindgen/pull/4020)

* Increase default stack size for spawned threads from 1 to 2 MB.
  [#3995](https://github.com/rustwasm/wasm-bindgen/pull/3995)

* Deprecated parameters to `default` (`init`) and `initSync` in favor of an object.
  [#3995](https://github.com/rustwasm/wasm-bindgen/pull/3995)

* Update `AbortSignal` and `AbortController` according to the WHATWG specification.
  [#4026](https://github.com/rustwasm/wasm-bindgen/pull/4026)

* Update the Indexed DB API.
  [#4027](https://github.com/rustwasm/wasm-bindgen/pull/4027)

* `UnwrapThrowExt for Result` now makes use of the required `Debug` bound to display the error as well.
  [#4035](https://github.com/rustwasm/wasm-bindgen/pull/4035)
  [#4049](https://github.com/rustwasm/wasm-bindgen/pull/4049)

* MSRV of CLI tools bumped to v1.76. This does not affect libraries like `wasm-bindgen`, `js-sys` and `web-sys`!
  [#4037](https://github.com/rustwasm/wasm-bindgen/pull/4037)

* Filtered files in published crates, significantly reducing the package size and notably excluding any bash files.
  [#4046](https://github.com/rustwasm/wasm-bindgen/pull/4046)

* Deprecated `JsStatic` in favor of `#[wasm_bindgen(thread_local)]`, which creates a `std::thread::LocalKey`. The syntax is otherwise the same.
  [#4057](https://github.com/rustwasm/wasm-bindgen/pull/4057)

* Removed `impl Deref for JsStatic` when compiling with `cfg(target_feature = "atomics")`, which was unsound.
  [#4057](https://github.com/rustwasm/wasm-bindgen/pull/4057)

* Updated the WebGPU WebIDL to the current draft as of 2024-08-05.
  [#4062](https://github.com/rustwasm/wasm-bindgen/pull/4062)

* Use object URLs for linked modules without `--split-linked-modules`.
  [#4067](https://github.com/rustwasm/wasm-bindgen/pull/4067)

### Fixed

* Copy port from headless test server when using `WASM_BINDGEN_TEST_ADDRESS`.
  [#3873](https://github.com/rustwasm/wasm-bindgen/pull/3873)

* Fix `catch` not being thread-safe.
  [#3879](https://github.com/rustwasm/wasm-bindgen/pull/3879)

* Fix MSRV compilation.
  [#3927](https://github.com/rustwasm/wasm-bindgen/pull/3927)

* Fix `clippy::empty_docs` lint.
  [#3946](https://github.com/rustwasm/wasm-bindgen/pull/3946)

* Fix missing target features in module when enabling reference types or multi-value transformation.
  [#3967](https://github.com/rustwasm/wasm-bindgen/pull/3967)

* Fixed Rust values getting GC'd while still borrowed.
  [#3940](https://github.com/rustwasm/wasm-bindgen/pull/3940)

* Fixed Rust values not getting GC'd if they were created via. a constructor.
  [#3940](https://github.com/rustwasm/wasm-bindgen/pull/3940)

* Fix triggering `clippy::mem_forget` lint in exported structs.
  [#3985](https://github.com/rustwasm/wasm-bindgen/pull/3985)

* Fix MDN links to static interface methods.
  [#4010](https://github.com/rustwasm/wasm-bindgen/pull/4010)

* Fixed Deno support.
  [#3990](https://github.com/rustwasm/wasm-bindgen/pull/3990)

* Fix `__wbindgen_thread_destroy()` ignoring parameters.
  [#3995](https://github.com/rustwasm/wasm-bindgen/pull/3995)

* Fix `no_std` support and therefor compiling with `default-features = false`.
  [#4005](https://github.com/rustwasm/wasm-bindgen/pull/4005)

* Fix byte order for big-endian platforms.
  [#4015](https://github.com/rustwasm/wasm-bindgen/pull/4015)

* Allow ex/importing structs, functions and parameters named with raw identifiers.
  [#4025](https://github.com/rustwasm/wasm-bindgen/pull/4025)

* Implement a more reliable way to detect the stack pointer.
  [#4036](https://github.com/rustwasm/wasm-bindgen/pull/4036)

* `#[track_caller]` is now always applied on `UnwrapThrowExt` methods when not targeting `wasm32-unknown-unknown`.
  [#4042](https://github.com/rustwasm/wasm-bindgen/pull/4042)

* Fixed linked modules emitting snippet files when not using `--split-linked-modules`.
  [#4066](https://github.com/rustwasm/wasm-bindgen/pull/4066)

--------------------------------------------------------------------------------

## [0.2.92](https://github.com/rustwasm/wasm-bindgen/compare/0.2.91...0.2.92)

Released 2024-03-04

### Added

* Add bindings for `RTCPeerConnectionIceErrorEvent`.
  [#3835](https://github.com/rustwasm/wasm-bindgen/pull/3835)

* Add bindings for `CanvasState.reset()`, affecting `CanvasRenderingContext2D` and `OffscreenCanvasRenderingContext2D`.
  [#3844](https://github.com/rustwasm/wasm-bindgen/pull/3844)

* Add `TryFrom` implementations for `Number`, that allow losslessly converting from 64- and 128-bits numbers.
  [#3847](https://github.com/rustwasm/wasm-bindgen/pull/3847)

* Add support for `Option<*const T>`, `Option<*mut T>` and `NonNull<T>`.
  [#3852](https://github.com/rustwasm/wasm-bindgen/pull/3852)
  [#3857](https://github.com/rustwasm/wasm-bindgen/pull/3857)

* Allow overriding the URL used for headless tests by setting `WASM_BINDGEN_TEST_ADDRESS`.
  [#3861](https://github.com/rustwasm/wasm-bindgen/pull/3861)

### Fixed

* Make .wasm output deterministic when using `--reference-types`.
  [#3851](https://github.com/rustwasm/wasm-bindgen/pull/3851)

* Don't allow invalid Unicode scalar values in `char`.
  [#3866](https://github.com/rustwasm/wasm-bindgen/pull/3866)

--------------------------------------------------------------------------------

## [0.2.91](https://github.com/rustwasm/wasm-bindgen/compare/0.2.90...0.2.91)

Released 2024-02-06

### Added

* Added bindings for the `RTCRtpTransceiver.setCodecPreferences()` and unstable bindings for the `RTCRtpEncodingParameters.scalabilityMode`.
  [#3828](https://github.com/rustwasm/wasm-bindgen/pull/3828)

* Add unstable bindings for the FileSystemAccess API
  [#3810](https://github.com/rustwasm/wasm-bindgen/pull/3810)

* Added support for running tests in shared and service workers with `wasm_bindgen_test_configure!` `run_in_shared_worker` and `run_in_service_worker`.
  [#3804](https://github.com/rustwasm/wasm-bindgen/pull/3804)

* Accept the `--skip` flag with `wasm-bindgen-test-runner`.
  [#3803](https://github.com/rustwasm/wasm-bindgen/pull/3803)

* Introduce environment variable `WASM_BINDGEN_TEST_NO_ORIGIN_ISOLATION` to disable origin isolation for `wasm-bindgen-test-runner`.
  [#3807](https://github.com/rustwasm/wasm-bindgen/pull/3807)

* Add bindings for `USBDevice.forget()`.
  [#3821](https://github.com/rustwasm/wasm-bindgen/pull/3821)

### Changed

* Stabilize `ClipboardEvent`.
  [#3791](https://github.com/rustwasm/wasm-bindgen/pull/3791)

* Use immutable buffers in `SubtleCrypto` methods.
  [#3797](https://github.com/rustwasm/wasm-bindgen/pull/3797)

* Deprecate `wasm_bindgen_test_configure!`s `run_in_worker` in favor of `run_in_dedicated_worker`.
  [#3804](https://github.com/rustwasm/wasm-bindgen/pull/3804)

* Updated the WebGPU WebIDL to the current draft as of 2024-01-30. Note that this retains the previous update's workaround for `GPUPipelineError`, and holds back an update to the `buffer` argument of the `GPUQueue.{writeBuffer,writeTexture}` methods.
  [#3816](https://github.com/rustwasm/wasm-bindgen/pull/3816)

* Deprecate `--weak-refs` and `WASM_BINDGEN_WEAKREF` in favor of automatic run-time detection.
  [#3822](https://github.com/rustwasm/wasm-bindgen/pull/3822)

### Fixed

* Fixed UB when freeing strings received from JS if not using the default allocator.
  [#3808](https://github.com/rustwasm/wasm-bindgen/pull/3808)

* Fixed temporary folder detection by `wasm-bindgen-test-runner` on MacOS.
  [#3817](https://github.com/rustwasm/wasm-bindgen/pull/3817)

* Fixed using `#[wasm_bindgen(js_name = default)]` with `#[wasm_bindgen(module = ...)]`.
  [#3823](https://github.com/rustwasm/wasm-bindgen/pull/3823)

* Fixed nightly build of `wasm-bindgen-futures`.
  [#3827](https://github.com/rustwasm/wasm-bindgen/pull/3827)

--------------------------------------------------------------------------------

## [0.2.90](https://github.com/rustwasm/wasm-bindgen/compare/0.2.89...0.2.90)

Released 2024-01-06

### Fixed

* Fix JS shim default path detection for the no-modules target.
  [#3748](https://github.com/rustwasm/wasm-bindgen/pull/3748)

### Added

* Add bindings for `HTMLFormElement.requestSubmit()`.
  [#3747](https://github.com/rustwasm/wasm-bindgen/pull/3747)

* Add bindings for `RTCRtpSender.getCapabilities(DOMString)` method, `RTCRtpCapabilities`, `RTCRtpCodecCapability` and `RTCRtpHeaderExtensionCapability`.
  [#3737](https://github.com/rustwasm/wasm-bindgen/pull/3737)

* Add bindings for `UserActivation`.
  [#3719](https://github.com/rustwasm/wasm-bindgen/pull/3719)

* Add unstable bindings for the Compression Streams API.
  [#3752](https://github.com/rustwasm/wasm-bindgen/pull/3752)

### Changed

* Stabilize File System API.
  [#3745](https://github.com/rustwasm/wasm-bindgen/pull/3745)

* Stabilize `QueuingStrategy`.
  [#3753](https://github.com/rustwasm/wasm-bindgen/pull/3753)

### Fixed

* Fixed a compiler error when using `#[wasm_bindgen]` inside `macro_rules!`.
  [#3725](https://github.com/rustwasm/wasm-bindgen/pull/3725)

### Removed

* Removed Gecko-only `InstallTriggerData` and Gecko-internal `FlexLineGrowthState`, `GridDeclaration`, `GridTrackState`,
  `RtcLifecycleEvent` and `WebrtcGlobalStatisticsReport` features.
  [#3723](https://github.com/rustwasm/wasm-bindgen/pull/3723)

--------------------------------------------------------------------------------

## [0.2.89](https://github.com/rustwasm/wasm-bindgen/compare/0.2.88...0.2.89)

Released 2023-11-27.

### Added

* Add additional constructor to `DataView` for `SharedArrayBuffer`.
  [#3695](https://github.com/rustwasm/wasm-bindgen/pull/3695)

* Stabilize `wasm_bindgen::module()`.
  [#3690](https://github.com/rustwasm/wasm-bindgen/pull/3690)

### Fixed

* The DWARF section is now correctly modified instead of leaving it in a broken state.
  [#3483](https://github.com/rustwasm/wasm-bindgen/pull/3483)

* Fixed an issue where `#[wasm_bindgen]` automatically derived the `TryFrom` trait for any struct, preventing custom `TryFrom<JsValue>` implementations. It has been updated to utilize a new `TryFromJsValue` trait instead.
  [#3709](https://github.com/rustwasm/wasm-bindgen/pull/3709)

* Update the TypeScript signature of `__wbindgen_thread_destroy` to indicate that it's parameters are optional.
  [#3703](https://github.com/rustwasm/wasm-bindgen/pull/3703)

### Removed

* Removed Gecko-internal dictionary bindings `Csp`, `CspPolicies`, `CspReport` and `CspReportProperties`.
  [#3721](https://github.com/rustwasm/wasm-bindgen/pull/3721)

--------------------------------------------------------------------------------

## [0.2.88](https://github.com/rustwasm/wasm-bindgen/compare/0.2.87...0.2.88) (YANKED)

Released 2023-11-01

### Added

* Add bindings for `RTCRtpTransceiverInit.sendEncodings`.
  [#3642](https://github.com/rustwasm/wasm-bindgen/pull/3642)

* Add bindings for the Web Locks API to `web-sys`.
  [#3604](https://github.com/rustwasm/wasm-bindgen/pull/3604)

* Add bindings for `ViewTransition` to `web-sys`.
  [#3598](https://github.com/rustwasm/wasm-bindgen/pull/3598)

* Extend `AudioContext` with unstable features supporting audio sink configuration.
  [#3433](https://github.com/rustwasm/wasm-bindgen/pull/3433)

* Add bindings for `WebAssembly.Tag` and `WebAssembly.Exception`.
  [#3484](https://github.com/rustwasm/wasm-bindgen/pull/3484)

* Re-export `wasm-bindgen` from `js-sys`, `web-sys` and `wasm-bindgen-futures`.
  [#3466](https://github.com/rustwasm/wasm-bindgen/pull/3466)
  [#3601](https://github.com/rustwasm/wasm-bindgen/pull/3601)

* Re-export `js-sys` from `web-sys` and `wasm-bindgen-futures`.
  [#3466](https://github.com/rustwasm/wasm-bindgen/pull/3466)
  [#3601](https://github.com/rustwasm/wasm-bindgen/pull/3601)

* Add bindings for async variants of `Atomics.wait`.
  [#3504](https://github.com/rustwasm/wasm-bindgen/pull/3504)

* Add bindings for `WorkerGlobalScope.performance`.
  [#3506](https://github.com/rustwasm/wasm-bindgen/pull/3506)

* Add support for installing pre-built artifacts of `wasm-bindgen-cli`
  via `cargo binstall wasm-bindgen-cli`.
  [#3544](https://github.com/rustwasm/wasm-bindgen/pull/3544)

* Add bindings for `RTCDataChannel.id`.
  [#3547](https://github.com/rustwasm/wasm-bindgen/pull/3547)

* Add bindings for `HTMLElement.inert`.
  [#3557](https://github.com/rustwasm/wasm-bindgen/pull/3557)

* Add unstable bindings for the Prioritized Task Scheduling API.
  [#3566](https://github.com/rustwasm/wasm-bindgen/pull/3566)

* Add bindings for `CssStyleSheet` constructor and `replace(_sync)` methods.
  [#3573](https://github.com/rustwasm/wasm-bindgen/pull/3573)

* Add bindings for `CanvasTransform.setTransform(DOMMatrix2DInit)`.
  [#3580](https://github.com/rustwasm/wasm-bindgen/pull/3580)

* Add a `crate` attribute to the `wasm_bindgen_test` proc-macro to specify a
  non-default path to the `wasm-bindgen-test` crate.
  [#3593](https://github.com/rustwasm/wasm-bindgen/pull/3593)

* Add support for passing `Vec`s of exported Rust types and strings to/from JS.
  [#3554](https://github.com/rustwasm/wasm-bindgen/pull/3554)

* Implement `TryFrom<JsValue>` for exported Rust types and strings.
  [#3554](https://github.com/rustwasm/wasm-bindgen/pull/3554)

* Handle the `#[ignore = "reason"]` attribute with the `wasm_bindgen_test`
  proc-macro and accept the `--include-ignored` flag with `wasm-bindgen-test-runner`.
  [#3644](https://github.com/rustwasm/wasm-bindgen/pull/3644)

* Added missing additions to the Notification API.
  [#3667](https://github.com/rustwasm/wasm-bindgen/pull/3667)

### Changed

* Updated the WebGPU WebIDL.
  The optional `message` argument of [`GPUPipelineError`](https://www.w3.org/TR/webgpu/#gpupipelineerror)'s constructor has been manually specified as a required argument,
  because required arguments occurring after optional arguments are currently not supported by the generator.
  [#3480](https://github.com/rustwasm/wasm-bindgen/pull/3480)

* Replaced `curl` with `ureq`. By default we now use Rustls instead of OpenSSL.
  [#3511](https://github.com/rustwasm/wasm-bindgen/pull/3511)

* Changed mutability of the argument `buffer` in `write` functions to immutable for `FileSystemSyncAccessHandle` and `FileSystemWritableFileStream`.
  It was also automatically changed for `IdbFileHandle`, which is deprecated.
  [#3537](https://github.com/rustwasm/wasm-bindgen/pull/3537)

* Changed behavior when compiling to `wasm32-wasi` to match `wasm32-emscripten` and
  non-Wasm targets, generating a stub that panics when called rather than a wasm-
  bindgen placeholder.
  [#3233](https://github.com/rustwasm/wasm-bindgen/pull/3233)

* Changed constructor implementation in generated JS bindings, it is now
  possible to override methods from generated JS classes using inheritance.
  When exported constructors return `Self`.
  [#3562](https://github.com/rustwasm/wasm-bindgen/pull/3562)

* Made `wasm-bindgen` forwards-compatible with the standard C ABI.
  [#3595](https://github.com/rustwasm/wasm-bindgen/pull/3595)

* Changed the design of the internal `WasmAbi` trait. Rather than marking a type
  which can be passed directly as a parameter/result to/from JS, it now lets
  types specify how they can be split into / recreated from multiple primitive
  types which are then passed to/from JS.
  `WasmPrimitive` now serves the old function of `WasmAbi`, minus allowing
  `#[repr(C)]` types.
  [#3595](https://github.com/rustwasm/wasm-bindgen/pull/3595)

* Use `queueMicrotask` in `wasm-bindgen-futures` for scheduling tasks on the next tick.
  If that is not available, use the previous `Promise.then` mechanism as a fallback.
  This should avoid quirks, like exceptions thrown get now properly reported
  as normal exceptions rather than as rejected promises.
  [#3611](https://github.com/rustwasm/wasm-bindgen/pull/3611)

* Improved TypeScript bindings to accurately reference Rust enum types in function signatures,
  enhancing type safety and compatibility.
  [#3647](https://github.com/rustwasm/wasm-bindgen/pull/3647)

* Throw an error on enum name collisions, previously only one enum would be emitted.
  [#3669](https://github.com/rustwasm/wasm-bindgen/pull/3669)

### Fixed

* Fixed `wasm_bindgen` macro to handle raw identifiers in field names.
  [#3621](https://github.com/rustwasm/wasm-bindgen/pull/3621)

* Fixed bindings and comments for `Atomics.wait`.
  [#3509](https://github.com/rustwasm/wasm-bindgen/pull/3509)

* Fixed `wasm_bindgen_test` macro to handle raw identifiers in test names.
  [#3541](https://github.com/rustwasm/wasm-bindgen/pull/3541)

* Fixed Cargo license field to follow the SPDX 2.1 license expression standard.
  [#3529](https://github.com/rustwasm/wasm-bindgen/pull/3529)

* Use fully qualified paths in the `wasm_bindgen_test` macro.
  [#3549](https://github.com/rustwasm/wasm-bindgen/pull/3549)

* Fixed bug allowing JS primitives to be returned from exported constructors.
  [#3562](https://github.com/rustwasm/wasm-bindgen/pull/3562)

* Fixed optional parameters in JSDoc.
  [#3577](https://github.com/rustwasm/wasm-bindgen/pull/3577)

* Use re-exported `js-sys` from `wasm-bindgen-futures` to account for
  non-default path specified by the `crate` attribute in `wasm_bindgen_futures`
  proc-macro.
  [#3601](https://github.com/rustwasm/wasm-bindgen/pull/3601)

* Fix bug with function arguments coming from `macro_rules!`.
  [#3625](https://github.com/rustwasm/wasm-bindgen/pull/3625)

* Fix some calls to `free()` missing alignment.
  [#3639](https://github.com/rustwasm/wasm-bindgen/pull/3639)

* Fix wrong ABI for raw pointers.
  [#3655](https://github.com/rustwasm/wasm-bindgen/pull/3655)

### Removed

* Removed `ReadableStreamByobReader::read_with_u8_array()` because it doesn't work with Wasm.
  [#3582](https://github.com/rustwasm/wasm-bindgen/pull/3582)

* Removed `GetNotificationOptions`, `NotificationBehavior` and `Notification.get()` because
  they don't exist anymore.

--------------------------------------------------------------------------------

## [0.2.87](https://github.com/rustwasm/wasm-bindgen/compare/0.2.86...0.2.87)

Released 2023-06-12.

### Added

* Implemented `IntoIterator` for `Array`.
  [#3477](https://github.com/rustwasm/wasm-bindgen/pull/3477)

### Changed

* Deprecate `HtmlMenuItemElement` and parts of `HtmlMenuElement`.
  [#3448](https://github.com/rustwasm/wasm-bindgen/pull/3448)

* Stabilize `ResizeObserver`.
  [#3459](https://github.com/rustwasm/wasm-bindgen/pull/3459)

### Fixed

* Take alignment into consideration during (de/re)allocation.
  [#3463](https://github.com/rustwasm/wasm-bindgen/pull/3463)

--------------------------------------------------------------------------------

## 0.2.86

Released 2023-05-16.

[changes](https://github.com/rustwasm/wasm-bindgen/compare/0.2.85...0.2.86)

--------------------------------------------------------------------------------

## 0.2.85

Released 2023-05-09.

[changes](https://github.com/rustwasm/wasm-bindgen/compare/0.2.84...0.2.85)

--------------------------------------------------------------------------------

## 0.2.84

Released 2023-02-01.

[changes](https://github.com/rustwasm/wasm-bindgen/compare/0.2.83...0.2.84)

--------------------------------------------------------------------------------

## 0.2.83

Released 2022-09-12.

[changes](https://github.com/rustwasm/wasm-bindgen/compare/0.2.82...0.2.83)

--------------------------------------------------------------------------------

## 0.2.82

Released 2022-07-25.

[changes](https://github.com/rustwasm/wasm-bindgen/compare/0.2.81...0.2.82)

--------------------------------------------------------------------------------

## 0.2.81

Released 2022-06-14.

[changes](https://github.com/rustwasm/wasm-bindgen/compare/0.2.80...0.2.81)

--------------------------------------------------------------------------------

## 0.2.80

Released 2022-04-04.

[changes](https://github.com/rustwasm/wasm-bindgen/compare/0.2.79...0.2.80)

--------------------------------------------------------------------------------

## 0.2.79

Released 2022-01-19.

[changes](https://github.com/rustwasm/wasm-bindgen/compare/0.2.78...0.2.79)

--------------------------------------------------------------------------------

## 0.2.78

Released 2021-09-15.

[changes](https://github.com/rustwasm/wasm-bindgen/compare/0.2.77...0.2.78)

--------------------------------------------------------------------------------

## 0.2.77

Released 2021-09-08.

[changes](https://github.com/rustwasm/wasm-bindgen/compare/0.2.76...0.2.77)

--------------------------------------------------------------------------------

## 0.2.76

Released 2021-08-19.

[changes](https://github.com/rustwasm/wasm-bindgen/compare/0.2.75...0.2.76)

--------------------------------------------------------------------------------

## 0.2.75

Released 2021-08-02.

[changes](https://github.com/rustwasm/wasm-bindgen/compare/0.2.74...0.2.75)

--------------------------------------------------------------------------------

## 0.2.74

Released 2021-05-10.

[changes](https://github.com/rustwasm/wasm-bindgen/compare/0.2.73...0.2.74)

--------------------------------------------------------------------------------

## 0.2.73

Released 2021-03-29.

[changes](https://github.com/rustwasm/wasm-bindgen/compare/0.2.72...0.2.73)

--------------------------------------------------------------------------------

## 0.2.72

Released 2021-03-18.

[changes](https://github.com/rustwasm/wasm-bindgen/compare/0.2.71...0.2.72)

--------------------------------------------------------------------------------

## 0.2.71

Released 2021-02-26.

[changes](https://github.com/rustwasm/wasm-bindgen/compare/0.2.70...0.2.71)

--------------------------------------------------------------------------------

## 0.2.70

Released 2021-01-25.

[changes](https://github.com/rustwasm/wasm-bindgen/compare/0.2.69...0.2.70)

--------------------------------------------------------------------------------

## 0.2.69

Released 2020-11-30.

### Added

* Unstable bindings for WebBluetooth have been added.
  [#2311](https://github.com/rustwasm/wasm-bindgen/pull/2311)

* Unstable bindings for WebUSB have been added.
  [#2345](https://github.com/rustwasm/wasm-bindgen/pull/2345)

* Renaming a struct field with `js_name` is now supported.
  [#2360](https://github.com/rustwasm/wasm-bindgen/pull/2360)

* The WebGPU WebIDL has been updated.
  [#2353](https://github.com/rustwasm/wasm-bindgen/pull/2353)

### Fixed

* The ImageCapture APIs of web-sys have been moved to unstable and were fixed.
  [#2348](https://github.com/rustwasm/wasm-bindgen/pull/2348)

* Bindings for `waitAsync` have been updated.
  [#2362](https://github.com/rustwasm/wasm-bindgen/pull/2362)

--------------------------------------------------------------------------------

## 0.2.68

Released 2020-09-08.

### Added

* Add userVisibleOnly property to PushSubscriptionOptionsInit.
  [#2288](https://github.com/rustwasm/wasm-bindgen/pull/2288)

### Fixed

* TypeScript files now import `*.wasm` instead of bare files.
  [#2283](https://github.com/rustwasm/wasm-bindgen/pull/2283)

* Usage of `externref` now appropriately resizes the table by using 2x the
  previous capacity, fixing a performance issue with lots of externref objects.
  [#2294](https://github.com/rustwasm/wasm-bindgen/pull/2294)

* Compatibility with the latest Firefox WebDriver has been fixed.
  [#2301](https://github.com/rustwasm/wasm-bindgen/pull/2301)

* Non deterministic output with closures has been fixed.
  [#2304](https://github.com/rustwasm/wasm-bindgen/pull/2304)

### Updated

* The WebGPU WebIDL was updated.
  [#2267](https://github.com/rustwasm/wasm-bindgen/pull/2267)

--------------------------------------------------------------------------------

## 0.2.67

Released 2020-07-28.

### Added

* A `--reference-types` flag was added to the CLI.
  [#2257](https://github.com/rustwasm/wasm-bindgen/pull/2257)

### Fixed

* Breakage with `Closure::forget` in 0.2.66 was fixed.
  [#2258](https://github.com/rustwasm/wasm-bindgen/pull/2258)

--------------------------------------------------------------------------------

## 0.2.66

Released 2020-07-28.

### Added

* Reverse mappings from value to name are now available in JS bindings of enums.
  [#2240](https://github.com/rustwasm/wasm-bindgen/pull/2240)

### Fixed

* Functions using a return pointer in threaded programs now correctly load and
  store return values in a way that doesn't interfere with other threads.
  [#2249](https://github.com/rustwasm/wasm-bindgen/pull/2249)

* Support for weak references has been updated and a `--weak-refs` flag is now
  available in the CLI for enabling weak references.
  [#2248](https://github.com/rustwasm/wasm-bindgen/pull/2248)

--------------------------------------------------------------------------------

## 0.2.65

Released 2020-07-15.

### Added

* Functions from JS can now be natively imported as `async` and will use
  promises under the hood.
  [#2196](https://github.com/rustwasm/wasm-bindgen/pull/2196)

### Changed

* Encoding for the reference types proposal has been updated to the latest
  version of the spec.
  [#2234](https://github.com/rustwasm/wasm-bindgen/pull/2234)

--------------------------------------------------------------------------------

## 0.2.64

Released 2020-06-29.

### Added

* Nested namespaces for imports can now be specified.
  [#2105](https://github.com/rustwasm/wasm-bindgen/pull/2105)

* A `deno` target has been added.
  [#2176](https://github.com/rustwasm/wasm-bindgen/pull/2176)

### Fixed

* Getters/setters that consume the original object have been fixed to invalidate
  the object correctly.
  [#2172](https://github.com/rustwasm/wasm-bindgen/pull/2172)

* Compatibility with nightly threading in LLVM has been fixed.
  [#2183](https://github.com/rustwasm/wasm-bindgen/pull/2183)

* Trailing space in generated doc comments is now removed.
  [#2210](https://github.com/rustwasm/wasm-bindgen/pull/2210)

--------------------------------------------------------------------------------

## 0.2.63

Released 2020-05-27.

### Added

* A new example about using WebRTC has been added.
  [#2131](https://github.com/rustwasm/wasm-bindgen/pull/2131)

* The `Blob.stream()` method has been added.
  [#2140](https://github.com/rustwasm/wasm-bindgen/pull/2140)
  [#2142](https://github.com/rustwasm/wasm-bindgen/pull/2142)

### Changed

* The encoding and implementation of WebAssembly reference types has been sync'd
  with the latest upstream specification.
  [#2125](https://github.com/rustwasm/wasm-bindgen/pull/2125)

### Fixed

* Test functions names will no longer collide with test intrinsic names.
  [#2123](https://github.com/rustwasm/wasm-bindgen/pull/2123)

* Fixed warnings with `#[must_use]` types in generated code.
  [#2144](https://github.com/rustwasm/wasm-bindgen/pull/2144)

* Fixed compatibility with latest Rust nightlies.
  [#2159](https://github.com/rustwasm/wasm-bindgen/pull/2159)

--------------------------------------------------------------------------------

## 0.2.62

Released 2020-05-01.

### Fixed

* Usage of `require` has been fixed with Webpack 5.
  [#2115](https://github.com/rustwasm/wasm-bindgen/pull/2115)

--------------------------------------------------------------------------------

## 0.2.61

Released 2020-04-29.

### Added

* Exported Rust `enum` types can now be renamed with `js_name`.
  [#2071](https://github.com/rustwasm/wasm-bindgen/pull/2071)

* More comments are copied to JS/TS files, and comments should no longer
  accidentally have escape sequences in them.
  [#2070](https://github.com/rustwasm/wasm-bindgen/pull/2070)

* Experimental bindings for the Clipboard browser APIs have been added.
  [#2100](https://github.com/rustwasm/wasm-bindgen/pull/2100)

### Changed

* WebGPU bindings have been updated.
  [#2080](https://github.com/rustwasm/wasm-bindgen/pull/2080)

* `setBindGroup` methods for WebIDL now take immutable slices instead of mutable
  slices.
  [#2087](https://github.com/rustwasm/wasm-bindgen/pull/2087)

* JS code generation for `catch` functions has been improved.
  [#2098](https://github.com/rustwasm/wasm-bindgen/pull/2098)

* Usage of NPM dependencies with the `web` target is no longer an error.
  [#2103](https://github.com/rustwasm/wasm-bindgen/pull/2103)

### Fixed

* Combining `js_name` with `getter` and `setter` has now been fixed.
  [#2074](https://github.com/rustwasm/wasm-bindgen/pull/2074)

* Importing global names which conflict with other namespaces should now work
  correctly.
  [#2057](https://github.com/rustwasm/wasm-bindgen/pull/2057)

* Acquiring the global JS object has been fixed for Firefox extension content
  scripts.
  [#2099](https://github.com/rustwasm/wasm-bindgen/pull/2099)

* The output of `wasm-bindgen` is now compatible with Webpack 5 and the updated
  version of the Wasm ESM integration specification.
  [#2110](https://github.com/rustwasm/wasm-bindgen/pull/2099)

--------------------------------------------------------------------------------

## 0.2.60

Released 2020-03-25.

### Added

* The `js_sys` types are now more accurately reflected in TypeScript.
  [#2028](https://github.com/rustwasm/wasm-bindgen/pull/2028)

* The timeout in `wasm-bindgen-test-runner`'s timeout can now be configured via
  `WASM_BINDGEN_TEST_TIMEOUT`.
  [#2036](https://github.com/rustwasm/wasm-bindgen/pull/2036)

* WebIDL for WebXR has been added.
  [#2000](https://github.com/rustwasm/wasm-bindgen/pull/2000)

### Changed

* The WebIDL for WebGPU has been updated.
  [#2037](https://github.com/rustwasm/wasm-bindgen/pull/2037)

--------------------------------------------------------------------------------

## 0.2.59

Released 2020-03-03.

### Added

* The `js_sys::Number` type now has a number of JS-number associated constants
  on it now.
  [#1965](https://github.com/rustwasm/wasm-bindgen/pull/1965)

* The `getTransform` method on `CanvasRenderingContext2D` has been added.
  [#1966](https://github.com/rustwasm/wasm-bindgen/pull/1966)

* Initial experimental support was added for electron targets with a new
  `--omit-imports` flag.
  [#1958](https://github.com/rustwasm/wasm-bindgen/pull/1958)

* Optional struct fields are now reflected idiomatically in TypeScript.
  [#1990](https://github.com/rustwasm/wasm-bindgen/pull/1990)

* Typed arrays in `js_sys` now have `get_index` and `set_index` methods.
  [#2001](https://github.com/rustwasm/wasm-bindgen/pull/2001)

* The `web_sys::Blob` type has been updated with `arrayBuffer` and `text`
  methods.
  [#2008](https://github.com/rustwasm/wasm-bindgen/pull/2008)

* Support for unstable browser interfaces has now been added. By compiling
  `web_sys` with `--cfg web_sys_unstable_apis` (typically via `RUSTFLAGS`)
  you'll be able to access all bound WebIDL functions, even those like GPU
  support on the web, which has now also had its WebIDL updated.
  [#1997](https://github.com/rustwasm/wasm-bindgen/pull/1997)

* The compile time for `web_sys` has been massively reduced by pre-generating
  Rust code from WebIDL. It is also readable now since it generates
  `#[wasm_bindgen]` annotations instead of expanded code.
  [#2012](https://github.com/rustwasm/wasm-bindgen/pull/2012)

* A new `typescript_type` attribute can be used to specify the TypeScript type
  for an `extern` type. [#2012](https://github.com/rustwasm/wasm-bindgen/pull/2012)

* It is now possible to use string values with `#[wasm_bindgen]` `enum`s.
  [#2012](https://github.com/rustwasm/wasm-bindgen/pull/2012)

* A new `skip_tyepscript` attribute is recognized to skip generating TypeScript
  bindings for a function or type.
  [#2016](https://github.com/rustwasm/wasm-bindgen/pull/2016)

### Changed

* More `uniformMatrix*` bindings now are whitelisted take shared slice instead
  of a mutable slice.
  [#1957](https://github.com/rustwasm/wasm-bindgen/pull/1957)

* Non-`dependency` keys in `package.json` are now ignored instead of error'd
  about.
  [#1969](https://github.com/rustwasm/wasm-bindgen/pull/1969)

* WebGPU has been removed from `web_sys` since it was outdated and didn't work
  anywhere anyway.
  [#1972](https://github.com/rustwasm/wasm-bindgen/pull/1972)

* The JS heap of objects managed by wasm-bindgen has had its definition
  tightended up a bit.
  [#1987](https://github.com/rustwasm/wasm-bindgen/pull/1987)

* The `self` identifier is no longer used on the `no-modules` target, making it a
  bit more flexible in more environments.
  [#1995](https://github.com/rustwasm/wasm-bindgen/pull/1995)

* The wasm-loading logic is now more flexible and can take promises as well.
  [#1996](https://github.com/rustwasm/wasm-bindgen/pull/1996)

* JS glue for closures is now deduplicated.
  [#2002](https://github.com/rustwasm/wasm-bindgen/pull/2002)

* The `web_sys` crate now emits more accurate TypeScript definitions using named
  types instead of `any` everywhere.
  [#1998](https://github.com/rustwasm/wasm-bindgen/pull/1998)

* The `send_with_u8_array` methods in `web_sys` are whitelisted to take shared
  slices instead of mutable slices.
  [#2015](https://github.com/rustwasm/wasm-bindgen/pull/2015)

--------------------------------------------------------------------------------

## 0.2.58

Released 2020-01-07.

### Added

* When using the `no-modules` output type the initialization path for the wasm
  file is now optional if it can be inferred from the current JS script.
  [#1938](https://github.com/rustwasm/wasm-bindgen/pull/1938)

### Fixed

* TypeScript for struct methods that have floats has been fixed.
  [#1945](https://github.com/rustwasm/wasm-bindgen/pull/1945)

--------------------------------------------------------------------------------

## 0.2.57

Released 2020-01-06.

### Fixed

* The `js_sys::Promise` type is now marked as `#[must_use]`
  [#1927](https://github.com/rustwasm/wasm-bindgen/pull/1927)

* Duplicate imports of the same name are now handled correctly again.
  [#1942](https://github.com/rustwasm/wasm-bindgen/pull/1942)

--------------------------------------------------------------------------------

## 0.2.56

Released 2019-12-20.

### Added

* Added a `#[wasm_bindgen(inspectable)]` attribute for exported objects to
  generate `toJSON` and `toString` implementations.
  [#1876](https://github.com/rustwasm/wasm-bindgen/pull/1876)

* Support for the most recent interface types proposal has been implemented.
  [#1882](https://github.com/rustwasm/wasm-bindgen/pull/1882)

* Initial support for async iterators has been added.
  [#1895](https://github.com/rustwasm/wasm-bindgen/pull/1895)

* Support for an `async` start function was added.
  [#1905](https://github.com/rustwasm/wasm-bindgen/pull/1905)

* `Array::iter` and `Array::to_vec` methods were added to js-sys.
  [#1909](https://github.com/rustwasm/wasm-bindgen/pull/1909)

### Fixed

* Another webkit-specific WebIDL construct was fixed in web-sys.
  [#1865](https://github.com/rustwasm/wasm-bindgen/pull/1865)

--------------------------------------------------------------------------------

## 0.2.55

Released 2019-11-19.

### Fixed

* Running `wasm-bindgen` over empty anyref modules now works again.
  [#1861](https://github.com/rustwasm/wasm-bindgen/pull/1861)

* Support for multi-value JS engines has been fixed as a Wasm interface types
  polyfill.
  [#1863](https://github.com/rustwasm/wasm-bindgen/pull/1863)

--------------------------------------------------------------------------------

## 0.2.54

Released 2019-11-07.

### Added

* A safe `to_vec` method has been added for typed arrays.
  [#1844](https://github.com/rustwasm/wasm-bindgen/pull/1844)

* A unsafe method `view_mut_raw` has been added to typed arrays.
  [#1850](https://github.com/rustwasm/wasm-bindgen/pull/1850)

* The `HTMLImageElement` WebIDL has been updated with recent features.
  [#1842](https://github.com/rustwasm/wasm-bindgen/pull/1842)

* Binary crates are now supported and `fn main` will be automatically executed
  like the `start` function.
  [#1843](https://github.com/rustwasm/wasm-bindgen/pull/1843)

### Changed

* Some JS glue generation has been tweaked to avoid TypeScript warnings.
  [#1852](https://github.com/rustwasm/wasm-bindgen/pull/1852)

--------------------------------------------------------------------------------

## 0.2.53

Released 2019-10-29.

### Fixed

* A bug with the experimental support for multi-value interface types has been
  fixed.
  [#1839](https://github.com/rustwasm/wasm-bindgen/pull/1839)

--------------------------------------------------------------------------------

## 0.2.52

Released 2019-10-24.

### Added

* The support for wasm-interface-types now uses multi-value by default.
  [#1805](https://github.com/rustwasm/wasm-bindgen/pull/1805)

* The Worklet IDL has been updated.
  [#1817](https://github.com/rustwasm/wasm-bindgen/pull/1817)

* The HTMLInputElement type has selectionStart and selectionEnd properties now.
  [#1811](https://github.com/rustwasm/wasm-bindgen/pull/1811)

* An `unintern` function has been added to remove an interned string from the
  cache.
  [#1828](https://github.com/rustwasm/wasm-bindgen/pull/1828)

### Changed

* Some WebIDL indexing getters have been corrected to reflect that they can
  throw and/or return `undefined`
  [#1789](https://github.com/rustwasm/wasm-bindgen/pull/1789)

### Fixed

* A bug with `TextDecoder` and Safari has been fxied
  [#1789](https://github.com/rustwasm/wasm-bindgen/pull/1789)

--------------------------------------------------------------------------------

## 0.2.51

Released 2019-09-26.

### Added

* The `wasm-bindgen-futures` and `wasm-bindgen-test` crates now require Nightly
  Rust and have a new major version published as a result. These crates now
  support `async`/`await` by default, and they will be supported in the stable
  Rust 1.39.0 release. The previous versions of crates will continue to work on
  stable today.
  [#1741](https://github.com/rustwasm/wasm-bindgen/pull/1741)

* Using `#[wasm_bindgen]` on an `async` function will now work and return a
  `Promise` on the JS side of things.
  [#1754](https://github.com/rustwasm/wasm-bindgen/pull/1754)

* More helper methods for `js_sys::Array` have been added.
  [#1749](https://github.com/rustwasm/wasm-bindgen/pull/1749)

* Initial support for the WebAssembly multi-value proposal has been added.
  [#1764](https://github.com/rustwasm/wasm-bindgen/pull/1764)

* Constructors for `js_sys::Date` with optional parameters has been added.
  [#1759](https://github.com/rustwasm/wasm-bindgen/pull/1759)

* Headless tests can now be run against a remote webdriver client
  [#1744](https://github.com/rustwasm/wasm-bindgen/pull/1744)

### Changed

* The `passStringToWasm` function has been optimized for size.
  [#1736](https://github.com/rustwasm/wasm-bindgen/pull/1736)

### Fixed

* BOM markers will not be preserved when passing strings to/from wasm.
  [#1730](https://github.com/rustwasm/wasm-bindgen/pull/1730)

* Importing a `static` value which isn't a `JsValue` has been fixed.
  [#1784](https://github.com/rustwasm/wasm-bindgen/pull/1784)

* Converting `undefined` to a Rust value via `into_serde` has been fixed.
  [#1783](https://github.com/rustwasm/wasm-bindgen/pull/1783)

* Routine errors are no longer erroneously logged in debug mode.
  [#1788](https://github.com/rustwasm/wasm-bindgen/pull/1788)

--------------------------------------------------------------------------------

## 0.2.50

Released 2019-08-19.

### Added

* Experimental support with a `WASM_INTERFACE_TYPES=1` environment variable has
  been added to emit a Wasm Interface Types custom section, making the output of
  `wasm-bindgen` a single standalone WebAssembly file.
  [#1725](https://github.com/rustwasm/wasm-bindgen/pull/1725)

### Fixed

* Unrelated errors are now no longer accidentally swallowed by the
  `instantiateStreaming` fallback.
  [#1723](https://github.com/rustwasm/wasm-bindgen/pull/1723)

--------------------------------------------------------------------------------

## 0.2.49

Released 2019-08-14.

### Added

* Add binding for `Element.getElementsByClassName`.
  [#1665](https://github.com/rustwasm/wasm-bindgen/pull/1665)

* `PartialEq` and `Eq` are now implemented for all `web-sys` types.
  [#1673](https://github.com/rustwasm/wasm-bindgen/pull/1673)

* The `wasm-bindgen-futures` crate now has support for futures when the
  experimental WebAssembly threading feature is enabled.
  [#1514](https://github.com/rustwasm/wasm-bindgen/pull/1514)

* A new `enable-interning` feature is available to intern strings and reduce the
  cost of transferring strings across the JS/Rust boundary.
  [#1612](https://github.com/rustwasm/wasm-bindgen/pull/1612)

* The `wasm-bindgen` CLI has experimental support for reading native
  `webidl-bindings` custom sections and generating JS glue. This support is in
  addition to Rust's own custom sections and allows using `wasm-bindgen` with
  binaries produced by other than rustc possibly.
  [#1690](https://github.com/rustwasm/wasm-bindgen/pull/1690)

* New environment variables have been added to configure webdriver startup
  arguments.
  [#1703](https://github.com/rustwasm/wasm-bindgen/pull/1703)

* New `JsValue::{is_truthy,is_falsy}` methods are now available.
  [#1638](https://github.com/rustwasm/wasm-bindgen/pull/1638)

### Changed

* JS import shims are now skipped again when they are unnecessary.
  [#1654](https://github.com/rustwasm/wasm-bindgen/pull/1654)

* WebAssembly output files now directly embed the module/name for imports if
  supported for the target and the import, reducing JS shims even further.
  [#1689](https://github.com/rustwasm/wasm-bindgen/pull/1689)

### Fixed

* Support for threads have been updated for LLVM 9 and nightly Rust.
  [#1675](https://github.com/rustwasm/wasm-bindgen/pull/1675)
  [#1688](https://github.com/rustwasm/wasm-bindgen/pull/1688)

* The `anyref` passes in `wasm-bindgen` have seen a number of fixes to improve
  their correctness and get the full test suite running.
  [#1692](https://github.com/rustwasm/wasm-bindgen/pull/1692)
  [#1704](https://github.com/rustwasm/wasm-bindgen/pull/1704)

* Support for `futures-preview 0.3.0-alpha.18` has been added to
  `wasm-bindgen-futures`.
  [#1716](https://github.com/rustwasm/wasm-bindgen/pull/1716)

--------------------------------------------------------------------------------

## 0.2.48

Released 2019-07-11.

### Added

* All typed arrays now implement `From` for the corresponding Rust slice type,
  providing a safe way to create an instance which copies the data.
  [#1620](https://github.com/rustwasm/wasm-bindgen/pull/1620)

* `Function::bind{2,3,4}` are now available in `js-sys`.
  [#1633](https://github.com/rustwasm/wasm-bindgen/pull/1633)

### Changed

* More WebGL methods have been updated to use shared slices instead of mutable
  slices.
  [#1639](https://github.com/rustwasm/wasm-bindgen/pull/1639)

* When using the `bundler` target the import of the Wasm file now uses the
  `.wasm` extension to ensure a Wasm file is loaded.
  [#1646](https://github.com/rustwasm/wasm-bindgen/pull/1646)

* The old internal `Stack` trait has been removed since it is no longer used.
  [#1624](https://github.com/rustwasm/wasm-bindgen/pull/1624)

### Fixed

* The `js_sys::global()` accessor now attempts other strategies before falling
  back to a `Function` constructor which can violate some strict CSP settings.
  [#1650](https://github.com/rustwasm/wasm-bindgen/pull/1649)

* Dropping a `JsFuture` no longer logs a benign error to the console.
  [#1649](https://github.com/rustwasm/wasm-bindgen/pull/1649)

* Fixed an assertion which could happen in some modules when generating
  bindings.
  [#1617](https://github.com/rustwasm/wasm-bindgen/pull/1617)

--------------------------------------------------------------------------------

## 0.2.47

Released 2019-06-19.

### Changed

* The `HtmlHyperlinkElement` should now include more native methods after a
  small edit to the WebIDL.
  [#1604](https://github.com/rustwasm/wasm-bindgen/pull/1604)

* Duplicate names for getters/setters now have a first-class `wasm-bindgen`
  error.
  [#1605](https://github.com/rustwasm/wasm-bindgen/pull/1605)

### Fixed

* TypeScript definition of `init` with `--target web` now reflects that the
  first argument is optional.
  [#1599](https://github.com/rustwasm/wasm-bindgen/pull/1599)

* A panic with the futures 0.3 support has been fixed.
  [#1598](https://github.com/rustwasm/wasm-bindgen/pull/1598)

* More slice types are recognized as becoming immutable in some WebIDL methods.
  [#1602](https://github.com/rustwasm/wasm-bindgen/pull/1602)

* The function table is now no longer too aggressively removed.
  [#1606](https://github.com/rustwasm/wasm-bindgen/pull/1606)

--------------------------------------------------------------------------------

## 0.2.46

Released 2019-06-14.

### Added

* Bindings for `Array#flat` and `Array#flatMap` have been added.
  [#1573](https://github.com/rustwasm/wasm-bindgen/pull/1573)

* All `#[wasm_bindgen]` types now `AsRef` to themselves.
  [#1583](https://github.com/rustwasm/wasm-bindgen/pull/1583)

* When using `--target web` the path passed to `init` is no longer required.
  [#1579](https://github.com/rustwasm/wasm-bindgen/pull/1579)

### Fixed

* Some diagnostics related to compiler errors in `#[wasm_bindgen]` have been
  improved.
  [#1550](https://github.com/rustwasm/wasm-bindgen/pull/1550)

* The support for weak references has been updated to the current JS proposal.
  [#1557](https://github.com/rustwasm/wasm-bindgen/pull/1557)

* Documentation and feature gating for web-sys dictionaries has improved.
  [#1572](https://github.com/rustwasm/wasm-bindgen/pull/1572)

* Getter and setter TypeScript has been fixed.
  [#1577](https://github.com/rustwasm/wasm-bindgen/pull/1577)

* The `env_logger` crate and its tree of dependencies is no longer required to
  build `web-sys`.
  [#1586](https://github.com/rustwasm/wasm-bindgen/pull/1586)

--------------------------------------------------------------------------------

## 0.2.45

Released 2019-05-20.

### Fixed

* Using `__wbindgen_cb_forget` on `--target web` has been fixed.
  [#1544](https://github.com/rustwasm/wasm-bindgen/pull/1544)

### Changed

* More whitelists have been added for `web-sys` to use shared slices instead of
  mutable slices.
  [#1539](https://github.com/rustwasm/wasm-bindgen/pull/1539)

--------------------------------------------------------------------------------

## 0.2.44

Released 2019-05-16.

### Added

* Support for exporting "fields" on JS objects wrapping Rust structs which are
  hooked up to getters/setters has been added. This is in addition to `pub`
  struct fields and allows performing more complicated computations in
  getters/setters.
  [#1440](https://github.com/rustwasm/wasm-bindgen/pull/1440)

* Support for futures 0.3 (and `async` / `await` syntax) has been added to the
  `wasm-bindgen-futures` crate.
  [#1507](https://github.com/rustwasm/wasm-bindgen/pull/1507)

* Stacks of imported JS functions that throw and aren't marked `catch` are now
  logged in debug mode.
  [#1466](https://github.com/rustwasm/wasm-bindgen/pull/1466)

* A utility for counting the size of the `anyref` heap has been added.
  [#1521](https://github.com/rustwasm/wasm-bindgen/pull/1521)

* Passing ASCII-only strings to Wasm should now be significantly faster.
  [#1470](https://github.com/rustwasm/wasm-bindgen/pull/1470)

* The `selectionStart` and `selectionEnd` APIs of text areas have been enabled.
  [#1533](https://github.com/rustwasm/wasm-bindgen/pull/1533)

### Changed

* Some more methods in `web-sys` now take immutable slices instead of mutable
  ones.
  [#1508](https://github.com/rustwasm/wasm-bindgen/pull/1508)

* TypeScript bindings for `Option<T>` arguments now use `foo?` where possible.
  [#1483](https://github.com/rustwasm/wasm-bindgen/pull/1483)

### Fixed

* Unnecessary bindings to `__wbindgen_object_drop_ref` have been fixed.
  [#1504](https://github.com/rustwasm/wasm-bindgen/pull/1504)

* Some direct imports have been fixed for `--target web`.
  [#1503](https://github.com/rustwasm/wasm-bindgen/pull/1503)

* Both importing and exporting the same name has been fixed.
  [#1506](https://github.com/rustwasm/wasm-bindgen/pull/1506)

* TypeScript typings for `init` in `--target web` have been fixed.
  [#1520](https://github.com/rustwasm/wasm-bindgen/pull/1520)

* Calling a dropped `Closure` should no longer "segfault" but produce a clear
  error.
  [#1530](https://github.com/rustwasm/wasm-bindgen/pull/1530)

--------------------------------------------------------------------------------

## 0.2.43

Released 2019-04-29.

### Added

* Support for `isize` and `usize` arrays has been added.
  [#1448](https://github.com/rustwasm/wasm-bindgen/pull/1448)

* Support customizing `dyn_ref` and friends via a new `is_type_of` attribute and
  apply it to some `js_sys` bindings.
  [#1405](https://github.com/rustwasm/wasm-bindgen/pull/1405)
  [#1450](https://github.com/rustwasm/wasm-bindgen/pull/1450)
  [#1490](https://github.com/rustwasm/wasm-bindgen/pull/1490)

* A new `skip` attribute to `#[wasm_bindgen]` has been added to skip fields and
  methods when generating bindings.
  [#1410](https://github.com/rustwasm/wasm-bindgen/pull/1410)

* More bindings have been added to `web-sys` for interfaces tagged with
  `[NoInterfaceObject]` in WebIDL. These types always fail `dyn_ref` and friends
  and must be manually casted into.
  [#1449](https://github.com/rustwasm/wasm-bindgen/pull/1449)

* Added `Debug for JsFuture`.
  [#1477](https://github.com/rustwasm/wasm-bindgen/pull/1477)

* Initial bindings for `Atomics` and `SharedArrayBuffer` have been added to
  `js_sys`.
  [#1463](https://github.com/rustwasm/wasm-bindgen/pull/1463)

* Bindings for `Object.fromEntries` has been added to `js_sys`.
  [#1456](https://github.com/rustwasm/wasm-bindgen/pull/1456)

* Tuple structs exported to JS now have indexed struct properties.
  [#1467](https://github.com/rustwasm/wasm-bindgen/pull/1467)

* Binding for `new Function(args, body)` has been added to `js_sys`.
  [#1492](https://github.com/rustwasm/wasm-bindgen/pull/1492)

* Bindings for some variadic functions have been added to `js_sys`.
  [#1491](https://github.com/rustwasm/wasm-bindgen/pull/1491)

### Changed

* Many `js-sys` types have received various tweaks and improvements to ensure
  they're consistent and work similarly to native Rust types.
  [#1447](https://github.com/rustwasm/wasm-bindgen/pull/1447)
  [#1444](https://github.com/rustwasm/wasm-bindgen/pull/1444)
  [#1473](https://github.com/rustwasm/wasm-bindgen/pull/1473)

* Dummy types in `js-sys` only used to namespace methods were removed and now
  modules are used for namespacing instead.
  [#1451](https://github.com/rustwasm/wasm-bindgen/pull/1451)

* Bindings in `web-sys` are formatted by default for ease of usage in IDEs.
  [#1461](https://github.com/rustwasm/wasm-bindgen/pull/1461)

### Fixed

* Documentation for Rust methods now show up in TypeScript as well.
  [#1472](https://github.com/rustwasm/wasm-bindgen/pull/1472)

--------------------------------------------------------------------------------

## 0.2.42

Released 2019-04-11.

### Fixed

* Fixed an issue in Firefox where using `encodeInto` accidentally caused empty
  strings to keep getting passed to Rust.
  [#1434](https://github.com/rustwasm/wasm-bindgen/pull/1434)

--------------------------------------------------------------------------------

## 0.2.41

Released 2019-04-10.

### Added

* Initial support for transitive NPM dependencies has been added.
  [#1305](https://github.com/rustwasm/wasm-bindgen/pull/1305)

* The `constructor` property of `Object` is now bound in `js-sys`.
  [#1403](https://github.com/rustwasm/wasm-bindgen/pull/1403)

* The `Closure` type now always implements `Debug`.
  [#1408](https://github.com/rustwasm/wasm-bindgen/pull/1408)

* Closures which take one `&T` argument are now supported. More implementations
  may be added in the future, but for now it's just one argument closures.
  [#1417](https://github.com/rustwasm/wasm-bindgen/pull/1417)

* The TypeScript bindings for `--web` now expose the `init` function.
  [#1412](https://github.com/rustwasm/wasm-bindgen/pull/1412)

* A `js_sys::JsString::is_valid_utf16` method has been added to handle unpaired
  surrogates in JS strings. Surrounding documentation has also been updated to
  document this potential pitfall.
  [#1416](https://github.com/rustwasm/wasm-bindgen/pull/1416)

* A `wasm_bindgen::function_table()` function has been added to expose the
  `WebAssembly.Table` and get access to it in Wasm code.
  [#1431](https://github.com/rustwasm/wasm-bindgen/pull/1431)

### Fixed

* Reexporting the `wasm_bindgen` macro in crates has been fixed.
  [#1359](https://github.com/rustwasm/wasm-bindgen/pull/1359)

* Returning `u32` to JS has been fixed where large `u32` values would show up in
  JS as large negative numbers.
  [#1401](https://github.com/rustwasm/wasm-bindgen/pull/1401)

* Manual instantiation with `WebAssembly.Module` has been fixed.
  [#1419](https://github.com/rustwasm/wasm-bindgen/pull/1419)

* Error message for non-`Copy` public struct fields has been improved.
  [#1430](https://github.com/rustwasm/wasm-bindgen/pull/1430)

### Changed

* Performance of passing strings to Rust in Node.js has been improved.
  [#1391](https://github.com/rustwasm/wasm-bindgen/pull/1391)

* Performance of `js_sys::try_iter` has been improved.
  [#1393](https://github.com/rustwasm/wasm-bindgen/pull/1393)

* Performance of using `TextEncoder#encodeInto` has been improved.
  [#1414](https://github.com/rustwasm/wasm-bindgen/pull/1414)

--------------------------------------------------------------------------------

## 0.2.40

Released 2019-03-21.

### Added

* TypeScript and JS generation will now attempt to preserve argument names in
  the generated JS where possible.
  [#1344](https://github.com/rustwasm/wasm-bindgen/pull/1344)

* Enable `Option<T>` support for enums defined in WebIDL.
  [#1350](https://github.com/rustwasm/wasm-bindgen/pull/1350)

* Add a `raw_module` attribute to `#[wasm_bindgen]` which is the same as
  `module` except doesn't attempt to recognize `./`, `../`, `or `/` prefixed
  paths.
  [#1353](https://github.com/rustwasm/wasm-bindgen/pull/1353)

* The `wasm-bindgen` CLI flags have now all been renamed under a `--target`
  flag. Instead of `--web` you'll now pass `--target web`, for example. This
  increases consistency between the `wasm-bindgen` and `wasm-pack` CLI.
  [#1369](https://github.com/rustwasm/wasm-bindgen/pull/1369)

### Fixed

* Definitions for `TypedArray` imports of `js-sys` have been unified with a
  macro to improve consistency and fix future bugs.
  [#1371](https://github.com/rustwasm/wasm-bindgen/pull/1371)

* Usage of `--no-modules` in CloudFlare workers should now work by default.
  [#1384](https://github.com/rustwasm/wasm-bindgen/pull/1384)

* A use-after-free when a closure is reinvoked after being destroyed on the Rust
  die has been fixed.
  [#1385](https://github.com/rustwasm/wasm-bindgen/pull/1385)

* A bug causing nondeterministic generation of JS bindings has been fixed.
  [#1383](https://github.com/rustwasm/wasm-bindgen/pull/1383)

--------------------------------------------------------------------------------

## 0.2.39

Released 2018-03-13.

### Added

* Crates can now import locally written JS snippets to get bundled into the
  final output. See [RFC 6] for more details as well as the PR.
  [#1295](https://github.com/rustwasm/wasm-bindgen/pull/1295)

[RFC 6]: https://github.com/rustwasm/rfcs/pull/6

### Changed

* A typo in the return value of `slice` methods on typed arrays in `js-sys` was
  corrected.
  [#1321](https://github.com/rustwasm/wasm-bindgen/pull/1321)

* The directory specified by `--out-dir` is now created if it doesn't exist
  already.
  [#1330](https://github.com/rustwasm/wasm-bindgen/pull/1330)

### Fixed

* A bug where if `nom` was in a crate graph and was compiled with the
  `verbose-errors` feature has been fixed. Previously the `wasm-bindgen-webidl`
  crate wouldn't compile, and now it will.
  [#1338](https://github.com/rustwasm/wasm-bindgen/pull/1338)

--------------------------------------------------------------------------------

## 0.2.38

Released 2019-03-04.

### Added

* Support for `Option<RustStruct>` in `#[wasm_bindgen]` functions has now been
  added.
  [#1275](https://github.com/rustwasm/wasm-bindgen/pull/1275)

* Experimental support for the `anyref` type proposal in WebAssembly has now
  landed and is enabled with `WASM_BINDGEN_ANYREF=1`.
  [#1002](https://github.com/rustwasm/wasm-bindgen/pull/1002)

* Support for the new browser `TextEncode#encodeInto` API has been added.
  [#1279](https://github.com/rustwasm/wasm-bindgen/pull/1279)

* JS doc comments are now added to TypeScript bindings in addition to the JS
  bindings generated.
  [#1302](https://github.com/rustwasm/wasm-bindgen/pull/1302)

* Initial support for `FnOnce` closures has been added to the `Closure` type.
  [#1281](https://github.com/rustwasm/wasm-bindgen/pull/1281)

### Fixed

* Fixed an internal assert tripping when some modules were compiled with LTO.
  [#1274](https://github.com/rustwasm/wasm-bindgen/pull/1274)

* The `Context` type in the `wasm-bindgen-test` crate had its JS name changed to
  avoid conflicts with other crates that have a `Context` type being exported.
  [#1280](https://github.com/rustwasm/wasm-bindgen/pull/1280)

* The headless test runner for Safari on macOS High Sierra has been fixed.
  [#1298](https://github.com/rustwasm/wasm-bindgen/pull/1298)

### Changed

* The `wasm-bindgen` CLI tool now emits the `producers` section again with
  relevant bugs having been fixed in the meantime. The
  `--remove-producers-section` flag can continue to be used to omit emission of
  this section.
  [#1263](https://github.com/rustwasm/wasm-bindgen/pull/1263)

--------------------------------------------------------------------------------

## 0.2.37

Released 2019-02-15.

### Added

* The `HtmlMediaElement` type now exposes a `src_object` getter.
  [#1248](https://github.com/rustwasm/wasm-bindgen/pull/1248).

* The `js_sys::Reflect` type now has specializes getter/setters for `u32` and
  `f64` indices.
  [#1225](https://github.com/rustwasm/wasm-bindgen/pull/1225).

* A `--remove-producers-section` flag has been added to the CLI tool to, well,
  remove the `producers` section from the final Wasm file.
  [#1256](https://github.com/rustwasm/wasm-bindgen/pull/1256).

### Fixed

* The `wasm-bindgen` CLI tool will correctly strip DWARF debug information
  unless `--keep-debug` is passed.
  [#1255](https://github.com/rustwasm/wasm-bindgen/pull/1255).

### Changed

* The `wasm-bindgen` CLI tool no longer emits the `producers` custom section by
  default to work around a [webpack bug]. See
  [#1260](https://github.com/rustwasm/wasm-bindgen/pull/1260).

[webpack bug]: https://github.com/webpack/webpack/pull/8786

--------------------------------------------------------------------------------

## 0.2.36

Released 2019-02-12.

### Fixed

* Fixed a bug where using closures and LTO together caused a panic inside the
  `wasm-bindgen` CLI tool. See
  [#1244](https://github.com/rustwasm/wasm-bindgen/issues/1244).

--------------------------------------------------------------------------------

## 0.2.35

Released 2019-02-12.

### Changed

* `wasm-bindgen` now internally uses the `walrus` crate to perform its
  transformations of the Wasm that rustc/LLVM emits. See
  [#1237](https://github.com/rustwasm/wasm-bindgen/pull/1237).

### Fixed

* When `WebAssembly.instantiateStreaming` fails due to incorrect MIME type,
  *actually* properly recover. See
  [#1243](https://github.com/rustwasm/wasm-bindgen/pull/1243).

--------------------------------------------------------------------------------

## 0.2.34

Released 2019-02-11.

### Added

* Added support for optional `enum`s. See
  [#1214](https://github.com/rustwasm/wasm-bindgen/pull/1214).
* Added the `UnwrapThrowExt<T>` trait, which can enable smaller code sizes for
  panics. See [#1219](https://github.com/rustwasm/wasm-bindgen/pull/1219).

### Fixed

* Some `WebGlRenderingContext` methods are now whitelisted to use shared slices
  instead of exclusive slices. See
  [#1199](https://github.com/rustwasm/wasm-bindgen/pull/1199).
* Fixed TypeScript definitions for optional types. See
  [#1201](https://github.com/rustwasm/wasm-bindgen/pull/1201).
* Quiet clippy warnings inside generated code. See
  [1207](https://github.com/rustwasm/wasm-bindgen/pull/1207).
* Fixed using `cfg_attr` and `wasm_bindgen` together like `#[cfg_attr(...,
  wasm_bindgen)]`. See
  [1208](https://github.com/rustwasm/wasm-bindgen/pull/1208).
* The WebAudio example program was fixed. See
  [#1215](https://github.com/rustwasm/wasm-bindgen/pull/1215).
* Fixed logging HTML in `wasm-bindgen-test`. See
  [#1233](https://github.com/rustwasm/wasm-bindgen/pull/1233).
* When `WebAssembly.instantiateStreaming` fails due to incorrect MIME type,
  properly recover. See
  [#1235](https://github.com/rustwasm/wasm-bindgen/pull/1235).

--------------------------------------------------------------------------------

## 0.2.33

Released 2019-01-18.

### Added

* Improved the `Debug` output of `JsValue`
  [#1161](https://github.com/rustwasm/wasm-bindgen/pull/1161)

* Bindings for `JSON.stringify` and its optional arguments have been added
  [#1190](https://github.com/rustwasm/wasm-bindgen/pull/1190)

### Fixed

* A bug with windows binaries being released has ben resolved.

--------------------------------------------------------------------------------

## 0.2.32

Released 2019-01-16.

### Added

* Added support for Web IDL sequences. This enabled bindings generation for a
  couple more Web APIs. We generate functions for Web APIs that take sequences
  to accept any iterable, and for Web APIs that return sequences, a
  `js_sys::Array` is returned. See
  [#1152](https://github.com/rustwasm/wasm-bindgen/pull/1152) and
  [#1038](https://github.com/rustwasm/wasm-bindgen/issues/1038).
* The `wasm-bindgen-test` test runner will capture `console.debug`,
  `console.info`, and `console.warn` log messages and print them to `stdout`
  now. It already supported `console.log` and `console.error` and continues to
  support them. See
  [#1183](https://github.com/rustwasm/wasm-bindgen/issues/1183) and
  [#1184](https://github.com/rustwasm/wasm-bindgen/pull/1184).
* Added additional `--debug`-only assertions in the emitted JS glue for cases
  where an imported JS function that is not annotated with
  `#[wasm_bindgen(catch)]` throws an exception. This should help catch some bugs
  earlier! See [#1179](https://github.com/rustwasm/wasm-bindgen/pull/1179).

### Fixed

* Fixed a bug where `#[wasm_bindgen_test]` tests would fail in non-headless Web
  browsers if they used `console.log`. See
  [#1167](https://github.com/rustwasm/wasm-bindgen/pull/1167).
* Fixed a bug where returning closures from exported functions sometimes
  resulted in a faulty error. See
  [#1174](https://github.com/rustwasm/wasm-bindgen/issues/1174) and
  [#1175](https://github.com/rustwasm/wasm-bindgen/pull/1175).
* Sometimes our generated TypeScript interface files had syntax errors in them
  (missing semicolons). This has been fixed. See
  [#1181](https://github.com/rustwasm/wasm-bindgen/pull/1181).

--------------------------------------------------------------------------------

## 0.2.31

Released 2019-01-09.

### Added

* A new `spawn_local` function has been added to the `wasm-bindgen-futures`
  crate.
  [#1148](https://github.com/rustwasm/wasm-bindgen/pull/1148)

* Built-in conversions are now available from typed arrays and Rust arrays.
  [#1147](https://github.com/rustwasm/wasm-bindgen/pull/1147)

### Fixed

* Some casing of dictionary properties in WebIDL has been fixed.
  [#1155](https://github.com/rustwasm/wasm-bindgen/pull/1155)

--------------------------------------------------------------------------------

## 0.2.30

Released 2019-01-07.

### Added

* The `wasm-bindgen` CLI now has an `--out-name` argument to name the output
  module.
  [#1084](https://github.com/rustwasm/wasm-bindgen/pull/1084)

* Support for importing the `default` export has been added.
  [#1106](https://github.com/rustwasm/wasm-bindgen/pull/1106)

### Changed

* All `web-sys` methods are now flagged as `structural`, fixing a few bindings.
  [#1117](https://github.com/rustwasm/wasm-bindgen/pull/1117)

### Fixed

* A small bug with LTO and closures has been fixed.
  [#1145](https://github.com/rustwasm/wasm-bindgen/pull/1145)

--------------------------------------------------------------------------------

## 0.2.29

Released 2018-12-04.

### Added

* Add a `#[wasm_bindgen(start)]` attribute to customize the `start` section of
  the Wasm module.
  [#1057](https://github.com/rustwasm/wasm-bindgen/pull/1057)

* Add support for producing the new "producers" section of Wasm binaries
  [#1041](https://github.com/rustwasm/wasm-bindgen/pull/1041)

* Add support a `typescript_custom_section` attribute for producing custom
  typescript abstractions
  [#1048](https://github.com/rustwasm/wasm-bindgen/pull/1048)

* Generate `*.d.ts` files for Wasm files in addition to the JS bindings
  [#1053](https://github.com/rustwasm/wasm-bindgen/pull/1053)

* Add a feature to assert that all attributes in `#[wasm_bindgen]` are used to
  help catch typos and mistakes
  [#1055](https://github.com/rustwasm/wasm-bindgen/pull/1055)

### Changed

* JS glue generation has received a few small optimizations such as removing
  shims and removing object allocations
  [#1033](https://github.com/rustwasm/wasm-bindgen/pull/1033)
  [#1030](https://github.com/rustwasm/wasm-bindgen/pull/1030)

* JS glue now just uses one array of JS objects instead of two
  [#1069](https://github.com/rustwasm/wasm-bindgen/pull/1069)

### Fixed

* Fix a typo in the `--no-modules` generated JS
  [#1045](https://github.com/rustwasm/wasm-bindgen/pull/1045)

--------------------------------------------------------------------------------

## 0.2.28

Released 2018-11-12.

### Added

* The `js_class` support is now supported on exported types to define a
  different class in JS than is named in Rust
  [#1012](https://github.com/rustwasm/wasm-bindgen/pull/1012)

* More WebIDL bindings are exposed with some internal restructuring to ignore
  unimplemented types at a different location
  [#1014](https://github.com/rustwasm/wasm-bindgen/pull/1014)

* All imported types now implement `Deref` to their first `extends` attribute
  (or `JsValue` if one isn't listed). This is intended to greatly improve the
  ergonomics of `web-sys` bindings by allowing easy access to parent class
  methods
  [#1019](https://github.com/rustwasm/wasm-bindgen/pull/1019)

* A new attribute, `final`, can be applied to JS imports. This attribute is
  relatively nuanced and [best explained in documentation][final-dox], but is
  added since `structural` is now the default
  [#1019](https://github.com/rustwasm/wasm-bindgen/pull/1019)

[final-dox]: https://rustwasm.github.io/wasm-bindgen/reference/attributes/on-js-imports/final.html

* A new CLI flag, `--remove-name-section`, can be passed to remove the wasm
  `name` section which contains the names of functions for debugging (typically
  not needed in release mode)
  [#1024](https://github.com/rustwasm/wasm-bindgen/pull/1024)

### Changed

* All imported functions are now `structural` by default. This shouldn't change
  the semantics of imported functions, only how they're invoked in the JS
  function shims that are generated by `wasm-bindgen`. More discussion can be
  founed on [RFC 5] and the PR
  [#1019](https://github.com/rustwasm/wasm-bindgen/pull/1019)

[RFC 5]: https://rustwasm.github.io/rfcs/005-structural-and-deref.html

* JS glue assertions for moved arguments are now only emitted in debug mode,
  which is still off by default
  [#1020](https://github.com/rustwasm/wasm-bindgen/pull/1020)

### Fixed

* Typescript generated bindings now correctly reflect `Option<T>` for more types
  [#1008](https://github.com/rustwasm/wasm-bindgen/pull/1008)

* The JS shim code generation has been optimized for `structural` bindings (now
  the default) to include fewer JS shims and more easily optimizable for JS
  engines
  [#1019](https://github.com/rustwasm/wasm-bindgen/pull/1019)

* Passing a `WebAssembly.Module` to the `--no-modules` constructor has been
  fixed
  [#1025](https://github.com/rustwasm/wasm-bindgen/pull/1025)

--------------------------------------------------------------------------------

## 0.2.27

Released 2018-10-29.

### Fixed

* Fixed an internal panic where the gc passes were being too aggressive
  [#995](https://github.com/rustwasm/wasm-bindgen/pull/995)

--------------------------------------------------------------------------------

## 0.2.26

Released 2018-10-29.

### Added

* The `TypedArray.slice` methods have now been bound in `js-sys`.
  [#956](https://github.com/rustwasm/wasm-bindgen/pull/956)

* The `Debug` and `Clone` traits are now implemented for `js_sys::Promise`.
  [#957](https://github.com/rustwasm/wasm-bindgen/pull/957)

* The `js_sys::DataView` type now exposes overloads to specify endianness.
  [#966](https://github.com/rustwasm/wasm-bindgen/pull/966)

* When using `--no-modules` a `WebAssembly.Module` can now be directly passed
  into the instantiation glue.
  [#969](https://github.com/rustwasm/wasm-bindgen/pull/969)

### Fixed

* The `JsValue` type is no longer considered `Send`.
  [#955](https://github.com/rustwasm/wasm-bindgen/pull/955)

* The generated JS glue is now more robust in the face of missing APIs.
  [#959](https://github.com/rustwasm/wasm-bindgen/pull/959)

* An issue with the latest version of `safaridriver` used to run headless tests
  has been resolved.
  [#991](https://github.com/rustwasm/wasm-bindgen/pull/991)

--------------------------------------------------------------------------------

## 0.2.25

Released 2018-10-10.

### Fixed

* Using `wasm-bindgen` will no longer unconditionally pull in Rust's default
  allocator for Wasm (dlmalloc) regardless if you configured a custom global
  allocator (eg wee_alloc).
  [#947](https://github.com/rustwasm/wasm-bindgen/pull/947)

* Fixed web-sys build on some Windows machines.
  [#943](https://github.com/rustwasm/wasm-bindgen/issues/943)

* Fixed generated ES class bindings to Rust structs that were only referenced
  through struct fields.
  [#948](https://github.com/rustwasm/wasm-bindgen/issues/948)

--------------------------------------------------------------------------------

## 0.2.24

Released 2018-10-05.

### Added

* Constructors for types in `web-sys` should now have better documentation.

* A new `vendor_prefix` attribute in `#[wasm_bindgen]` is supported to bind APIs
  on the web which may have a vendor prefix (like `webkitAudioContext`). This is
  then subsequently used to fix `AudioContext` usage in Safari.

* The `#[wasm_bindgen(extends = Foo)]` attribute now supports full paths, so you
  can also say `#[wasm_bindgen(extends = foo::Bar)]` and such.

### Changed

* The `Closure<T>` type is now optimized when the underlying closure is a ZST.
  The type now no longer allocates memory in this situation.

* The documentation now has a list of caveats for browser support, including how
  `TextEncoder` and `TextDecoder` are not implemented in Edge. If you're using
  webpack there's a listed strategy available, and improvements to the polyfill
  strategy are always welcome!

* The `BaseAudioContext` and `AudioScheduledSourceNode` types in `web-sys` have
  been deprecated as they don't exist in Safari or Edge.

### Fixed

* Fixed the `#[wasm_bindgen_test]`'s error messages in a browser to correctly
  escape HTML-looking output.

* WebIDL Attributes on `Window` are now correctly bound to not go through
  `Window.prototype` which doesn't exist but instead use a `structural`
  definition.

* Fixed a codegen error when the `BorrowMut` trait was in scope.

* Fixed TypeScript generation for constructors of classes, it was accidentally
  producing a syntactially invalid file!

--------------------------------------------------------------------------------

## 0.2.23

Released 2018-09-26.

### Added

* [This is the first release of the `web-sys`
  crate!](https://rustwasm.github.io/2018/09/26/announcing-web-sys.html)

* Added support for unions of interfaces and non-interfaces in the WebIDL
  frontend.

* Added a policy for inclusion of new ECMAScript features in `js-sys`: the
  feature must be in stage 4 or greater for us to support it.

* Added some documentation about size profiling and optimization with
  `wasm-bindgen` to the guide.

* Added the `Clamped<T>` type for generating JavaScript `Uint8ClampedArray`s.

* CI is now running on beta! Can't wait for the `rustc` release trains to roll
  over, so we can run CI on stable too!

* Added the `js_sys::try_iter` function, which checks arbitrary JS values for
  compliance with the JS iteration protocol, and if they are iterable, converts
  them into an iterator over the JS values that they yield.

### Changed

* We now only generate null checks on methods on the JS side when in debug
  mode. For safety we will always null check on the Rust side, however.

* Improved error messages when defining setters that don't start with `set_` and
  don't use `js_name = ...`.

* Improved generated code for classes in a way that avoids an unnecessary
  allocation with static methods that return `Self` but are not the "main"
  constructor.

* **BREAKING:** `js_sys::Reflect` APIs are all fallible now. This is because
  reflecting on `Proxy`s whose trap handlers throw an exception can cause any of
  the reflection APIs to throw. Accordingly, `js_sys` has been bumped from
  `0.2.X` to `0.3.X`.

### Fixed

* The method of ensuring that `__wbindgen_malloc` and `__wbindgen_free` are
  always emitted in the `.wasm` binary, regardless of seeming reachability is
  now zero-overhead.

--------------------------------------------------------------------------------

## 0.2.22

Released 2018-09-21

### Added

* The `IntoIterator` trait is now implemented for JS `Iterator` types
* A number of variadic methods in `js-sys` have had explicit arities added.
* The guide has been improved quite a bit as well as enhanced with more examples
* The `js-sys` crate is now complete! Thanks so much to everyone involved to
  help fill out all the APIs.
* Exported Rust functions with `#[wasm_bindgen]` can now return a `Result` where
  the `Err` payload is raised as an exception in JS.

### Fixed

* An issue with running `wasm-bindgen` on crates that have been compiled with
  LTO has been resolved.

--------------------------------------------------------------------------------

## 0.2.21

Released 2018-09-07

### Added

* Added many more bindings for `WebAssembly` in the `js-sys` crate.

### Fixed

* The "names" section of the Wasm binary is now correctly preserved by
  wasm-bindgen.

--------------------------------------------------------------------------------

## 0.2.20

Released 2018-09-06

### Added

* All of `wasm-bindgen` is configured to compile on stable Rust as of the
  upcoming 1.30.0 release, scheduled for October 25, 2018.
* The underlying `JsValue` of a `Closure<T>` type can now be extracted at any
  time.
* Initial and experimental support was added for modules that have shared memory
  (use atomic instructions).

### Removed

* The `--wasm2asm` flag of `wasm2es6js` was removed because the `wasm2asm` tool
  has been removed from upstream Binaryen. This is replaced with the new
  `wasm2js` tool from Binaryen.

### Fixed

* The "schema" version for wasm-bindgen now changes on all publishes, meaning we
  can't forget to update it. This means that the crate version and CLI version
  must exactly match.
* The `wasm-bindgen` crate now has a `links` key which forbids multiple versions
  of `wasm-bindgen` from being linked into a dependency graph, fixing obscure
  linking errors with a more first-class error message.
* Binary releases for Windows has been fixed.

--------------------------------------------------------------------------------

## 0.2.19 (and 0.2.18)

Released 2018-08-27.

### Added

* Added bindings to `js-sys` for some `WebAssembly` types.
* Added bindings to `js-sys` for some `Intl` types.
* Added bindings to `js-sys` for some `String` methods.
* Added an example of using the WebAudio APIs.
* Added an example of using the `fetch` API.
* Added more `extends` annotations for types in `js-sys`.
* Experimental support for `WeakRef` was added to automatically deallocate Rust
  objects when gc'd.
* Added support for executing `wasm-bindgen` over modules that import their
  memory.
* Added a global `memory()` function in the `wasm-bindgen` crate for accessing
  the JS object that represent wasm's own memory.

### Removed

* Removed `AsMut` implementations for imported objects.

### Fixed

* Fixed the `constructor` and `catch` attributes combined on imported types.
* Fixed importing the same-named static in two modules.

--------------------------------------------------------------------------------

## 0.2.17

Released 2018-08-16.

### Added

* Greatly expanded documentation in the wasm-bindgen guide.
* Added bindings to `js-sys` for `Intl.DateTimeFormat`
* Added a number of `extends` attributes for types in `js-sys`

### Fixed

* Fixed compile on latest nightly with latest `proc-macro2`
* Fixed compilation in some scenarios on Windows with paths in `module` paths

--------------------------------------------------------------------------------

## 0.2.16

Released 2018-08-13.

### Added

* Added the `wasm_bindgen::JsCast` trait, as described in [RFC #2][rfc-2].
* Added [the `#[wasm_bindgen(extends = ...)]` attribute][extends-attr] to
  describe inheritance relationships, as described in [RFC #2][rfc-2].
* Added support for receiving `Option<&T>` parameters from JavaScript in
  exported Rust functions and methods.
* Added support for receiving `Option<u32>` and other option-wrapped scalars.
* Added reference documentation to the guide for every `#[wasm_bindgen]`
  attribute and how it affects the generated bindings.
* Published the `wasm-bindgen-futures` crate for converting between JS
  `Promise`s and Rust `Future`s.

### Changed

* Overhauled the guide's documentation on passing JS closures to Rust, and Rust
  closures to JS.
* Overhauled the guide's documentation on using serde to serialize complex data
  to `JsValue` and deserialize `JsValue`s back into complex data.
* Static methods are now always bound to their JS class, as is required for
  `Promise`'s static methods.

### Removed

* Removed internal usage of `syn`'s `visit-mut` cargo feature, which should
  result in faster build times.

### Fixed

* Various usage errors for the `#[wasm_bindgen]` proc-macro are now properly
  reported with source span information, rather than `panic!()`s inside the
  proc-macro.
* Fixed a bug where taking a struct by reference and returning a slice resulted
  in lexical variable redeclaration errors in the generated JS glue. [#662][]
* The `#[wasm_bindgen(js_class = "....")]` attribute for binding methods to
  renamed imported JS classes now properly works with constructors.

[rfc-2]: https://rustwasm.github.io/rfcs/002-wasm-bindgen-inheritance-casting.html
[extends-attr]: https://rustwasm.github.io/wasm-bindgen/reference/attributes/on-js-imports/extends.html
[#662]: https://github.com/rustwasm/wasm-bindgen/pull/662

--------------------------------------------------------------------------------

## 0.2.15

Released 2018-07-26.

### Fixed

* Fixed `wasm-bindgen` CLI version mismatch checks that got broken in the last
  point release.

--------------------------------------------------------------------------------

## 0.2.14

Released 2018-07-25.

### Fixed

* Fixed compilation errors on targets that use
  Mach-O. [#545](https://github.com/rustwasm/wasm-bindgen/issues/545)

--------------------------------------------------------------------------------

## 0.2.13

Released 2018-07-22.

### Added

* Support the `#[wasm_bindgen(js_name = foo)]` attribute on exported functions
  and methods to allow renaming an export to JS. This allows JS to call it by
  one name and Rust to call it by another, for example using `camelCase` in JS
  and `snake_case` in Rust

### Fixed

* Compilation with the latest nightly compiler has been fixed (nightlies on and
  after 2018-07-21)

--------------------------------------------------------------------------------

## 0.2.12

Released 2018-07-19.

This release is mostly internal refactorings and minor improvements to the
existing crates and functionality, but the bigs news is an upcoming `js-sys` and
`web-sys` set of crates. The `js-sys` crate will expose [all global JS
bindings][js-all] and the `web-sys` crate will be generated from WebIDL to
expose all APIs browsers have. More info on this soon!

[js-all]: https://github.com/rustwasm/wasm-bindgen/issues/275

### Added

* Support for `Option<T>` was added where `T` can be a number of slices or
  imported types.
* Comments in Rust are now preserved in generated JS bindings, as well as
  comments being generated to indicate the types of arguments/return values.
* The online documentation has been reorganized [into a book][book].
* The generated JS is now formatted better by default for readability.
* A `--keep-debug` flag has been added to the CLI to retain debug sections by
  default. This happens by default when `--debug` is passed.

[book]: https://rustwasm.github.io/wasm-bindgen/

### Fixed

* Compilation with the latest nightly compiler has been fixed (nightlies on and
  after 2018-07-19)
* Declarations of an imported function in multiple crates have been fixed to not
  conflict.
* Compilation with `#![deny(missing_docs)]` has been fixed.

--------------------------------------------------------------------------------

## 0.2.11

Released 2018-05-24.

--------------------------------------------------------------------------------

## 0.2.10

Released 2018-05-17.

--------------------------------------------------------------------------------

## 0.2.9

Released 2018-05-11.
