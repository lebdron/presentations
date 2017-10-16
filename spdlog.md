### spdlog v0.12+

https://github.com/gabime/spdlog
+++

**spdlog** - very fast, header only, C++ logging library.

+++

Code example

```C++
auto console = spd::stdout_color_mt("console");
console->info("Welcome to spdlog!");
console->error("Some error message with arg{}..", 1);
```
