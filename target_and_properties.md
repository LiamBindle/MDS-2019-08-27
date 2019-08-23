
<h2 style="text-align: center">Targets and properties</h2>

(this is important) 


### Targets

- A target is a component of your project (i.e. a library or executable)
- Targets are created with
    ```cmake
        add_library(<target name> [STATIC | SHARED | MODULE]
            [EXCLUDE_FROM_ALL]
            [source1] [source2 ...]
        )
    ```
    and
    ```cmake
        add_executable(<target name> [EXCLUDE_FROM_ALL]
            [source1] [source2 ...]
        )
    ```
- And every target has properties


### Properties
<div style="text-align: left; width: 80%; display: block; margin-left: auto; margin-right: auto;">

- Target properties are defined in one of two scopes: `PRIVATE` or `INTERFACE`
- A target's properties serve two purposes:
    1. Private properties control how the target is built
    2. Interface properties pass requirements to dependent targets

<div style="text-align: center; font-size: 0.6em; margin: 20px auto;">

| Scope | Used internally? | Passed to dependents? |
|---|:---:|:---:|
| `PRIVATE` | <span style="color: green;">Yes</span> | <span style="color: red;">No</span> |
| `INTERFACE` | <span style="color: red;">No</span> | <span style="color: green;">Yes</span> |
| `PUBLIC` | <span style="color: green;">Yes</span> | <span style="color: green;">Yes</span> |

</div>

- The most important properties are for
    - Compiler definitions
    - Compiler options (flags)
    - Include directories
    - Link libraries
</div>


### Inheriting properties from dependencies
<!-- - Again, a target's interface properties pass suage requirements to dependents -->
- A target "inherits" interface properties from every target it links against
<img class="plain" data-src="images/target_link_libraries-2.png">
- So in

    ```cmake
    target_link_libraries(targetC
        PRIVATE targetA
        PUBLIC targetB
    )
    ```
- `targetC` gets interface properties from `targetA` and `targetB`
- Only interface properties from `targetB` and passed on to dependents of `targetC`