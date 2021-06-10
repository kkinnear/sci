# Changelog

For a list of breaking changes, check [here](#breaking-changes)

## Unreleased

## v0.2.5

### Enhancements / fixes

- Fix metadata on non-constant map literal expression [#546](https://github.com/borkdude/sci/issues/546)
- Support `:reload-all` [#552](https://github.com/borkdude/sci/issues/552)
- Support new kwargs handling from 1.11.0 [#553](https://github.com/borkdude/sci/issues/553).
- Allow dynamic `:doc` on `def`/`defn` [#554](https://github.com/borkdude/sci/issues/554).
- Fix metadata on nested evaluated map [#555](https://github.com/borkdude/sci/issues/555)
- Bug with protocol methods in record where later arg overrides "this" [#557](https://github.com/borkdude/sci/issues/557)
- Support :rename in :refer-clojure [#558](https://github.com/borkdude/sci/issues/558)
- Add `aset-...`, `delay?`, `bit-clear`
- Add `bound-fn` and `bound-fn*`
- Add arg count check for `clojure.core/for`

## v0.2.4

### New

- Detect cyclic load dependencies [#531](https://github.com/borkdude/sci/issues/531)
- Add `force`
- Add `dissoc!` ([@wilkerlucio](https://github.com/wilkerlucio))

### Enhancements / fixes

- BREAKING: Do not merge ex-data into sci error [#534](https://github.com/borkdude/sci/issues/534) ([@GreshamDanielStephens](https://github.com/GreshamDanielStephens))
- Pick fn arity independent of written order [#532](https://github.com/borkdude/sci/issues/532) ([@GreshamDanielStephens](https://github.com/GreshamDanielStephens))
- `(instance? clojure.lang.IAtom 1)` returns `true` [#537](https://github.com/borkdude/sci/issues/537)
- Fix `ns-unmap` on referred var [#539](https://github.com/borkdude/sci/issues/539)

## v0.2.3

### Enhancements / fixes

- if with falsy literal returns nil [#529](https://github.com/borkdude/sci/issues/529)

## v0.2.2

### Enhancements / fixes

- Fix error reporting in case of arity error [#518](https://github.com/borkdude/sci/issues/518)
- Shadowing record field names in protocol functions [#513](https://github.com/borkdude/sci/issues/513)
- Fix destructuring in protocol method for record [#512](https://github.com/borkdude/sci/issues/512)
- Faster processing of maps, sets and vectors [#482](https://github.com/borkdude/sci/issues/482)
- Prioritize current namespace vars in syntax quote [#509](https://github.com/borkdude/sci/issues/509)
- Fix ns-publics to not include refers [#520](https://github.com/borkdude/sci/issues/520)
- Add `refer-clojure` macro [#519](https://github.com/borkdude/sci/issues/519)
- Syntax quote resolves referred var incorrectly [#526](https://github.com/borkdude/sci/issues/526)
- Priorize referred vars over vars in current ns [#527](https://github.com/borkdude/sci/issues/527)

## v0.2.1

### Enhancements / fixes

- Improvements for using `type` on `defrecord` [#492](https://github.com/borkdude/sci/issues/492)
- Deref vars at analysis time that have `:inline` metadata in Clojure [#483](https://github.com/borkdude/sci/issues/483)
- Keep only location metadata for seqs and symbols [#488](https://github.com/borkdude/sci/issues/488)
- Conditionally defined vars should not have metadata [#496](https://github.com/borkdude/sci/issues/496)
- Fix interop on map [#506](https://github.com/borkdude/sci/issues/506)
- Performance improvements [#500](https://github.com/borkdude/sci/issues/500), [#502](https://github.com/borkdude/sci/issues/502), [#504](https://github.com/borkdude/sci/issues/504)
- Fix shadow-cljs warnings [#499](https://github.com/borkdude/sci/issues/499)

## v0.2.0

Thanks for contributing to this release:

[@lread](https://github.com/lread), [@patrick-galvin](https://github.com/patrick-galvin), [@SevereOverfl0w](https://github.com/SevereOverfl0w), [@djblue](https://github.com/djblue), [@kwrooijen](https://github.com/kwrooijen), [@sogaiu](https://github.com/sogaiu), [@joinr](https://github.com/joinr), [@RickMoynihan](https://github.com/RickMoynihan), [@galdober](https://github.com/galdober)

### Breaking changes

- Removed `:realize-max` and `:preset :termination-safe`. In the light of
  [#348](https://github.com/borkdude/sci/issues/348) it would be misleading to
  claim that sci can guarantee termination within reasonable time.

### New

- Add `class?`, `iterator-seq`, `remove-watch`, `realized?`, `clojure.walk/macroexpand-all`, `find-var`, `lazy-cat`, `bound?`, `*print-namespace-maps*`, `get-thread-bindings`, `var-get`, `var-set`, `with-local-vars`
- Add `fork` API function [#369](https://github.com/borkdude/sci/issues/369)
- Add API functions for parsing code and evaluating forms: `sci.core/reader`,
  `sci.core/parse-string`, `sci.core/parse-next`, `sci.core/eval-form` [#404](https://github.com/borkdude/sci/issues/404)
- Support implementing `IDeref`, `IAtom`, `IAtom2` (and CLJS equivalents) [#401](https://github.com/borkdude/sci/issues/401)
- Add API vars `print-meta`, `print-level` which can be used with
  `sci.core/binding` to control the dynamic var equivalent in sci programs
- Support calling `symbol` on a var [#453](https://github.com/borkdude/sci/issues/453)
- `:disable-arity-checks` option: when used, sci behaves similarly to CLJS/JS by
  not checking the provided number of arguments and allowing less or more for
  single and fixed arity functions
  [#460](https://github.com/borkdude/sci/issues/460)

### Enhancements / fixes

- Alter-var-root uses thread-bound value to update [#359](https://github.com/borkdude/sci/issues/359)
- Eval metadata on var created with defn [#371](https://github.com/borkdude/sci/issues/371)
- Metadata fn on var f fails if referring to f [#363](https://github.com/borkdude/sci/issues/363)
- Fix missing protocol methods [#367](https://github.com/borkdude/sci/issues/367) ([@patrick-galvin](https://github.com/patrick-galvin))
- Support multiple methods of protocol on defrecord
- Allow re-binding of core vars with clojure.core/with-redefs [#375](https://github.com/borkdude/sci/issues/375)
- Fix false dynamic binding [#379](https://github.com/borkdude/sci/issues/379)
- Don't eval record returned from reader function [#386](https://github.com/borkdude/sci/issues/386)
- Implement `->` and `as->` as normal macros [#390](https://github.com/borkdude/sci/issues/390), [#462](https://github.com/borkdude/sci/issues/462) ([@kwrooijen](https://github.com/kwrooijen))
- `defn` should not introduce local for name in body [#384](https://github.com/borkdude/sci/issues/384)
- Fix wrong arity in error message when calling macro [#392](https://github.com/borkdude/sci/issues/392)
- Throw when trying to redefine referred var [#398](https://github.com/borkdude/sci/issues/398)
- Fix for `use` [120175f](https://github.com/borkdude/sci/commit/120175f2efc0328e88a832e792db342a70558806)
- Fix importing protocol classes from namespaces with hyphens [#410](https://github.com/borkdude/sci/issues/410)
- Performance enhancements [#415](https://github.com/borkdude/sci/issues/415), [#452](https://github.com/borkdude/sci/issues/452), [#468](https://github.com/borkdude/sci/issues/468), [#470](https://github.com/borkdude/sci/issues/470), [#472](https://github.com/borkdude/sci/issues/472), [#473](https://github.com/borkdude/sci/issues/473), [#475](https://github.com/borkdude/sci/issues/475), [#478](https://github.com/borkdude/sci/issues/478), [#480](https://github.com/borkdude/sci/issues/480)
- Support top-level do emitted from macro [#421](https://github.com/borkdude/sci/issues/421)
- Support map constructor for maps [#431](https://github.com/borkdude/sci/issues/431)
- Partial support for multiple reified classes [323a257](https://github.com/borkdude/sci/commit/323a2574ec4d59a0544a829c1fa529fcbc110140)
- Fix calling literal symbol babashka/babashka#622
- Allow user-defined vars when def is allowed [#434](https://github.com/borkdude/sci/issues/434)
- Fix default destructuring with false [#436](https://github.com/borkdude/sci/issues/436)
- Fix reflection warning in multimethods code [#437](https://github.com/borkdude/sci/issues/437) ([@galdober](https://github.com/galdober))
- Support nested libspecs [#399](https://github.com/borkdude/sci/issues/399)
- Aliases in protocol functions should work [#440](https://github.com/borkdude/sci/issues/440)
- Allow users to override :line metadata [#443](https://github.com/borkdude/sci/issues/443)
- Support second arg (env) in `resolve`
- Preserve and eval reader meta on coll literals and functions [#447](https://github.com/borkdude/sci/issues/447), [#448](https://github.com/borkdude/sci/issues/448)
- Fix #js object reading [#449](https://github.com/borkdude/sci/issues/449)
- Support unmap for imported classes [#432](https://github.com/borkdude/sci/issues/432)
- Fix for reader conditional parsing borkdude/edamame#65
- Dotted field access for JS interop [#450](https://github.com/borkdude/sci/issues/450)
- Syntax checks for binding [#458](https://github.com/borkdude/sci/issues/458)
- Add `boolean?` to constant check [#465](https://github.com/borkdude/sci/issues/465) ([@kwrooijen](https://github.com/kwrooijen))
- Check macro var value at analysis time [#467](https://github.com/borkdude/sci/issues/467)
- Excluded clojure var still gets resolved to in syntax quote [#466](https://github.com/borkdude/sci/issues/466)

## v0.1.0 (2020-06-16)

Thank to [@jeroenvandijk](https://github.com/jeroenvandijk), [@jjttjj](https://github.com/jjttjj), [@justone](https://github.com/justone), [@sogaiu](https://github.com/sogaiu) and [@armincerf](https://github.com/armincerf) for
contributing.

### New

- Implement hierarchies (`derive` etc.) [#237](https://github.com/borkdude/sci/issues/237)
- Implement multimethods [#236](https://github.com/borkdude/sci/issues/236)
- Add `ns-interns`, `ns-imports`, `ns-refers`, `ns-map`, `all-ns`
- Add `do-template`
- Add `clojure.edn` namespace
- Add `promise` and `deliver` ([@jeroenvandijk](https://github.com/jeroenvandijk))
- Add `:readers` option to support data readers ([@jjttjj](https://github.com/jjttjj))
- Add `tagged-literal`
- Add `when-some` and `if-some` ([@justone](https://github.com/justone))
- Add `re-matcher`
- Add `re-groups` ([@sogaiu](https://github.com/sogaiu))
- Implement `read-string` + `eval` [#285](https://github.com/borkdude/sci/issues/285)
- Add `ns-unmap` ([@sogaiu](https://github.com/sogaiu))
- Support `*print-length*` [#294](https://github.com/borkdude/sci/issues/294)
- Add `while` macro [#296](https://github.com/borkdude/sci/issues/296)
- Add `clojure.repl/find-doc` [#304](https://github.com/borkdude/sci/issues/304)
- Add `clojure.repl/apropos` [#317](https://github.com/borkdude/sci/issues/317)
- Add `memoize`
- Add `load-string` [#307](https://github.com/borkdude/sci/issues/307)
- Add `clojure.repl/pst`
- Add `with-bindings` macro [#289](https://github.com/borkdude/sci/issues/289)
- Add `ns-resolve`
- Add `clojure.core/read` [#317](https://github.com/borkdude/sci/issues/317)
- Add `remove-ns` [#318](https://github.com/borkdude/sci/issues/318)
- Add `requiring-resolve` [#316](https://github.com/borkdude/sci/issues/316)
- Add `tagged-literal?` function ([@armincerf](https://github.com/armincerf))
- Support `with-redefs` [#325](https://github.com/borkdude/sci/issues/325)
- New `create-ns`, `new-macro-var`, `copy-var`, `init` and `eval-string*` API functions
- Add `enumeration-seq`
- Add `bean`
- Support GraalVM java11 [#332](https://github.com/borkdude/sci/issues/332)
- Support `*print-meta*` [#334](https://github.com/borkdude/sci/issues/334)
- Support `clojure.core/intern` [#336](https://github.com/borkdude/sci/issues/336)
- Defprotocol and defrecord support [#279](https://github.com/borkdude/sci/issues/279), [#319](https://github.com/borkdude/sci/issues/319)
- Add `double-array` and `short-array`
- Add support for `*print-level*`

## Enhancements / fixes

- Elide metadata from function results (this makes calling evaluated functions
  from JavaScript easier) [#259](https://github.com/borkdude/sci/issues/259)
- Eval metadata on vars (e.g. `(def ^{:test (fn [] \"foo\")} x)`).
- Syntax check on amount of args for `if` ([@jeroenvandijk](https://github.com/jeroenvandijk))
- Support namespace metadata [#269](https://github.com/borkdude/sci/issues/269)
- `require` can now be used as a function
- `find-ns` should return `nil` for non-existent namespace [#299](https://github.com/borkdude/sci/issues/299)
- Mark `dotimes` as termination-safe [#298](https://github.com/borkdude/sci/issues/298)
- Fix metadata on syntax-quoted values [#301](https://github.com/borkdude/sci/issues/301)
- Add support for `:refer :all` in namespace form [#297](https://github.com/borkdude/sci/issues/297)
- Support `:rename` in `:require` [#303](https://github.com/borkdude/sci/issues/303)
- Add support for `use` [#302](https://github.com/borkdude/sci/issues/302)
- `resolve` can now be used a function
- `loop` bindings can refer to previous ones
- JS interop improvements [#312](https://github.com/borkdude/sci/issues/312)
- Fix handling `atom` with metadata [#314](https://github.com/borkdude/sci/issues/314)
- Fix unqualified binding of `when` and `nth` in `for` macro
- More JS interop improvements ([@jeroenvandijk](https://github.com/jeroenvandijk))
- Fix for variadic recur [#321](https://github.com/borkdude/sci/issues/321)
- Fix for associative destructuring ([commit](https://github.com/borkdude/sci/commit/438ec15798f319f232d789b74b04ac25f15d540b))
- Add syntax check for `ns` macro: first arg is required and should be symbol
- Fix dynamic binding for functions
- Fix parser line numbers when using shebang
- Remove Java API, don't include AOT-ed sources in release
- Preserve location information in error when `NullPointerException` occurs
- Support alternative field access syntax `(. Integer -SIZE)` [#339](https://github.com/borkdude/sci/issues/339)
- Check syntax of `def` and report too many arguments [#340](https://github.com/borkdude/sci/issues/340)
- Fix alternative field access syntax `(Integer/SIZE)`
- Fix resolving var from other namespace via refer

## Prior to v0.1.0

Details about releases prior to v0.1.0 can be found
[here](https://github.com/borkdude/sci/releases).

## Breaking changes

### 0.2.4

-  Do not merge ex-data into sci error [#534](https://github.com/borkdude/sci/issues/534)

### >= 0.1.0

- Removed `:realize-max` and `:preset :termination-safe`. In the light of
  [#348](https://github.com/borkdude/sci/issues/348) it would be misleading to
  claim that sci can guarantee termination within reasonable time.

### v0.0.12

- `:row` and `:col` metadata have been renamed to `:line` and `:column` to be
  more compatible with Clojure.

### v0.0.11

- macros provided via options (functions marked with `:sci/macro` metadata) now
  have two additional arguments at the start: `&env` and `&form`.
