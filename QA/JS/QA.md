### 1.Javascript Interview Question: Why does [9,8,7,6][1,2] = 7 ?
ANS: The subsequent element [1,2] cannot function as an array; hence, it operates as an array subscript. In the context of a subscript operation, the contents do not constitute a delimited list of operands but rather a singular expression.

<i>In javascript, we can write expressions separated by a comma (,). and the result of the last expression will be returned.</i>

It's Mean return 2 of [1,2].

And Then [9,8,7,6][2] = 7. { index 2 of [9,8,7,6] is 7 }
