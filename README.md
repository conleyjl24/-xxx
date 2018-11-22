“[#lang racket]”
“[(define (in-dbs k n)]”
“[(letrec ([a (make-vector (* k n) 0)]]”
“[[init empty-sequence]]”
“[[seq (λ (t p)]”
“[(when (and (> t n) (= 0 (modulo n p)))]”
“[(set! init (sequence-append init (in-vector (vector-copy a 1 (add1 p))))))]”
  “[(unless (> t n)]”
“[(vector-set! a t (vector-ref a (- t p)))]”
“[(set! init (seq (add1 t) p))]”
 “[ (for ([j (in-range (add1 (vector-ref a (- t p))) k)])]”
“[(vector-set! a t j)]”
“[(set! init (seq (add1 t) t))))]”
 “[ init)])]”
“[(seq 1 1)))]”
“[(for/list ([b (in-dbs 10 4)]) b)]”
“[@477447]”
"[(*)]"
(*)

“[(for/list ([b (in-dbs 10 4)]) b)]”
		“[@477447]”
		"[(*)]"

(*)





