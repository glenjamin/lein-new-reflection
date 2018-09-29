# tl;dr

Do not enable `*warn-on-reflection*`, use `lein check instead`.

# Reflection Warning

I did

* Create project

    `lein new app test`

* Bump to clojure 1.6
* Enable warn on reflection
* Run the app

    `lein run 20`

Produces

    Reflection warning, /private/var/folders/5y/rjb0fch13hl03l3sljvph3k8qv25c1/T/form-init1204030887884725897.clj:1:1004 - call to static method invokeStaticMethod on clojure.lang.Reflector can't be resolved (argument types: unknown, java.lang.String, unknown).
    Hello, World!

# Detailed behaviour

1. As of Clojure 1.9.0, the warning appears on `lein run` but not on `lein ubejar` or `lein check`.
1. Introducing actual reflection problems cause errors to appear in `lein run`, `lein uberjar`, and `lein check`.
1. Removing the project setting for `*warn-on-reflection*` results in no warnings on `lein run` but they still appear on `lein check` if there are actual errors in the project.
1. From the previous points we can conclude that any reflection necessary for the project that makes it to the jar files generated would be catched by `lein check`.
1. Removing the project setting for `*warn-on-reflection*` and doing `lein check` regularly should avoid the annoyance of leiningen warnings on `lein run` while resulting in reflection free code. So that is a workaround to consider.

[HTH](https://xkcd.com/979/).
