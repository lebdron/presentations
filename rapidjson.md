### rapidjson v1.1.0+

https://github.com/miloyip/rapidjson
+++

**rapidjson** - a fast JSON parser/generator for C++.

+++

Example

```C++
#include "rapidjson/document.h"
#include "rapidjson/writer.h"
#include "rapidjson/stringbuffer.h"
#include <iostream>
using namespace rapidjson;
int main() {
    auto json = R"({"project":"rapidjson","stars":10})";
    Document d;
    d.Parse(json);
    Value& s = d["stars"];
    s.SetInt(s.GetInt() + 1);
    StringBuffer buffer;
    Writer<StringBuffer> writer(buffer);
    d.Accept(writer);
    std::cout << buffer.GetString() << std::endl;
    return 0;
}
```

@[7-9](Parse a JSON string into DOM.)
@[10-11](Modify it by DOM.)
@[12-14](Stringify the DOM.)
@[15](Output `{"project":"rapidjson","stars":11}`)
