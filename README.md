# clatern

Machine learning in Clojure as easy as 1,2,3
(work in progress)

## Usage

```clojure
(ns foo.example
  (:use clojure.core.matrix)
  (:use clojure.core.matrix.dataset)
  (:use clatern.core))

(def dmat (matrix [[1 350 "apartment"]
                  [2 300 "apartment"]
                  [3 300 "apartment"]
                  [4 50	"apartment"]
                  [4 500 "apartment"]
                  [4 400 "apartment"]
                  [5 450 "apartment"]
                  [7 850 "house"]
                  [7 900 "house"]
                  [7 1200 "house"]
                  [8 1500 "house"]
                  [9 1300 "house"]
                  [8 1240 "house"]
                  [10 1700 "house"]
                  [9 1000 "house"]
                  [1 800 "flat"]
                  [3 900 "flat"]
                  [2 700 "flat"]
                  [1 900 "flat"]
                  [2 1150 "flat"]
                  [1 1000 "flat"]
                  [2 1200 "flat"]
                  [1 1300 "flat"]]))

(def new-dmat (matrix [[1 400]
                       [10 1600]
                       [3 1200]
                       [2 750]]))

(def data (dataset ["rooms" "area" "output"] dmat))
(def new-data (dataset ["rooms" "area"] new-dmat))

(-> (new-model :knn)
    (fit data)
    (predict new-data))

=> #clojure.core.matrix.impl.dataset.DataSet{:column-names ["area" "rooms" "output"], :columns [[400 1600 1200 750] [1 10 3 2] ["apartment" "house" "house" "flat"]]}
```

## License

Copyright © 2014 Rinu Boney

Distributed under the Eclipse Public License either version 1.0 or (at
your option) any later version.