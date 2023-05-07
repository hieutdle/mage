## match versus if/else

[Reddit](https://www.reddit.com/r/rust/comments/w625ur/is_there_any_advantage_of_using_match_instead_of/)

Clarity and destructuring and makes exhaustiveness (examining every possible path) more obvious.

```rust
let light_value = match traffic_light { // I only have to read this line to know what we are branching on
    Red => 1,
    Yellow => 2,
    Green => 3,
    // _ => panic!("We don't need this line because Rust will check to make sure all cases is used")
};

let light_value2 = if traffic_light == Red { // I have to read way further down to know the logic of this if conditional
    1
} else if traffic_light == Yellow {
    2
} else { // I have to read up to here to know if the case statement is only about traffic_light. Also, did it handle all cases? What if TrafficLight added a new state?
    3
};
/*
} else if traffic_light == Green { // we can't just use this to assert exhaustiveness, as then we break the expression type check.
    3
} else {
    panic!("We can have a catch all else at the end, but then it means it is a runtime error")
}
*/
```


## let mut versus shadowing

