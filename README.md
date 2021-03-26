# Introduction
Reconstant lets you share constant and enum definitions between programming languages.

Constants are defined in a yaml file and converted to idiomatic definitions in multiple programming languages.

Supported outputs include C/CPP header files, Python3 (using the enum module), Python2, Javascript, VueMixins, Java, and Rust.

This is still a WIP. Feel free to open an issue on github with questions or a PR with support for additional languages.

# Example
## Create an input file
#### `test.yaml`
```yaml
constants:
- name: SOME_CONSTANT
  value: "this is a constant string"
- name: OTHER_CONSTANT
  value: 42

enums:
- name: SomeEnum
  values:
    - A
    - B
    - C
- name: OtherEnum
  values:
    - FOO
    - BAR

outputs:
  python:
    path: autogenerated_constants.py
  javascript:
    path: autogenerated_constants.js
  c:
    path: autogenerated_constants.h
  python2:
    path: autogenerated_constants_py2.py
  vue:
    path: autogenerated_vue_constants.js
  java:
    path: AutogeneratedConstants.java
```

## Install and run reconstant
```
pip install git+https://github.com/aantn/reconstant.git
reconstant test.yaml
```

## Generated Output Files
### Python
#### `autogenerated_constants.py`
```python
# autogenerated by reconstant - do not edit!
from enum import Enum

# constants
SOME_CONSTANT = "this is a constant string"
OTHER_CONSTANT = 42

# enums
class SomeEnum(Enum):
	A = 0
	B = 1
	C = 2

class OtherEnum(Enum):
	FOO = 0
	BAR = 1

```

### Javascript
#### `autogenerated_constants.js`
```javascript
// autogenerated by reconstant - do not edit!

// constants
export const SOME_CONSTANT = "this is a constant string"
export const OTHER_CONSTANT = 42

// enums
export const SomeEnum = {
	A : 0,
	B : 1,
	C : 2,
}
export const OtherEnum = {
	FOO : 0,
	BAR : 1,
}
```

### C/CPP
#### `autogenerated_constants.h`
```c
// autogenerated by reconstant - do not edit!
#ifndef AUTOGENERATED_CONSTANTS_H
#define AUTOGENERATED_CONSTANTS_H

// constants
const char* SOME_CONSTANT = "this is a constant string";
const int OTHER_CONSTANT = 42;

// enums
typedef enum { A, B, C } SomeEnum;
typedef enum { FOO, BAR } OtherEnum;

#endif /* AUTOGENERATED_CONSTANTS_H */
```

### Python2-Compatible Output
#### `autogenerated_constants_py2.py`
```python
# autogenerated by reconstant - do not edit!

# constants
SOME_CONSTANT = "this is a constant string"
OTHER_CONSTANT = 42

# enums
SOME_ENUM_A = 0
SOME_ENUM_B = 1
SOME_ENUM_C = 2
OTHER_ENUM_FOO = 0
OTHER_ENUM_BAR = 1
```

### Vue Mixins
#### `autogenerated_vue_constants.py`
```js
// autogenerated by reconstant - do not edit!

// constants
export const SOME_CONSTANT = "this is a constant string"
export const OTHER_CONSTANT = 42

// enums
export const SomeEnum = {
	A : 0,
	B : 1,
	C : 2,
}

SomeEnum.Mixin = {
  created () {
      this.SomeEnum = SomeEnum
  }
}
export const OtherEnum = {
	FOO : 0,
	BAR : 1,
}

OtherEnum.Mixin = {
  created () {
      this.OtherEnum = OtherEnum
  }
}
```

### Java
#### `AutogeneratedConstants.java`
```java
// autogenerated by reconstant - do not edit!
public final class AutogeneratedConstants {

// constants
	public static final String SOME_CONSTANT = "this is a constant string";
	public static final int OTHER_CONSTANT = 42;

// enums
	public enum SomeEnum {
		A, 
		B, 
		C
	}
	public enum OtherEnum {
		FOO, 
		BAR
	}

}
```

### Rust
#### `autogenerated_constants.rs`
```rust
// autogenerated by reconstant - do not edit!

// constants
pub const SOME_CONSTANT: &str = "this is a constant string";
pub const OTHER_CONSTANT: i32 = 42;

// enums
pub enum SomeEnum {
	A, 
	B, 
	C
}
pub enum OtherEnum {
	FOO, 
	BAR
}
```
