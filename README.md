# Lua Shared Adapter for GmodC
This is a small library that extracts all exported functions from lua_shared module. For use with C and [GmodC](https://github.com/Meow/gmodc).

This essentially exposes Lua C API.

## Example
```c
#include "lua_shared.h"

DLL_EXPORT int gmod13_open(lua_State *state) {
  luabase_t *LUA = lua_get_base(state);

  /* You must call this in order for the functions to load! */
  load_lua_shared();

  /* Use regular Lua API functions */
  luaL_loadstring(state, "print('test')");
  lua_call(state, 0, 0);

  return 0;
}
```
