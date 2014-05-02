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

