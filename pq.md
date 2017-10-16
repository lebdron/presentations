### pq

https://git.postgresql.org/git/postgresql

### pqxx 5.0.1+

https://github.com/jtv/libpqxx

+++

**pq** - C client library for PostgreSQL.

**pqxx** - C++ bindings for **pq**.

+++

We use `pq` to connect to PostgreSQL, which works as `WorldStateView` - aggregate of all transactions.

+++

Example

```C++
#include <iostream>
#include <pqxx/pqxx>
int main()
{
  try {
    pqxx::connection C;
    std::cout << "Connected to " << C.dbname() << std::endl;
    pqxx::work W(C);
    pqxx::result R = W.exec("SELECT name FROM employee");
    std::cout << "Found " << R.size() << "employees:\n";
    for (const auto row: R)
      std::cout << row[0].c_str() << std::endl;
  } catch (const std::exception &e) {
    std::cerr << e.what() << std::endl;
    return 1;
  }
  return 0;
}
```

@[2](include pqxx)
@[6](create connection to postgres)
@[8](work - analogue of transaction)
@[9](execute `select` query)
@[10-12](print result of query)
@[13](in case of any error - exception (descendant of `std::exception`) is thrown)
