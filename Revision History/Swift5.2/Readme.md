https://docs.swift.org/swift-book/GuidedTour/Compatibility.html

Updated for Swift 5.2
=====

Swift 5.2 업데이트 내용
-----

- Functions that return an opaque type require the Swift 5.1 runtime.
- The `try?` expression doesn’t introduce an extra level of optionality to expressions that already return optionals.
- Large integer literal initialization expressions are inferred to be of the correct integer type. For example, UInt64(`0xffff_ffff_ffff_ffff`) evaluates to the correct value rather than overflowing.
