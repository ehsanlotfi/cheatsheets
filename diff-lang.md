# Comprehensive Language & Ecosystem Cheatsheet
### JS/Node.js vs Go vs Python vs C# (.NET)

| Feature / Concept | JavaScript / Node.js | Go (Golang) | Python | C# (.NET) |
| :--- | :--- | :--- | :--- | :--- |
| **Project Config** | `package.json` | `go.mod` | `pyproject.toml` / `requirements.txt` | `.csproj` |
| **Lock File** | `package-lock.json` | `go.sum` | `poetry.lock` / `uv.lock` | `packages.lock.json` |
| **Package Manager** | `npm` / `pnpm` / `bun` | `go` CLI | `pip` / `poetry` / `uv` | `dotnet` CLI / `NuGet` |
| **Init Project** | `npm init -y` | `go mod init <module-path>` | `poetry init` / `uv init` | `dotnet new console` |
| **Install Package** | `npm install <pkg>` | `go get <pkg>` | `pip install <pkg>` | `dotnet add package <pkg>` |
| **Sync/Clean Deps** | `npm install` | `go mod tidy` | `pip install -r requirements.txt` | `dotnet restore` |
| **Deps Location** | `./node_modules` | Global Cache (`$GOPATH/pkg/mod`) | `.venv/lib/pythonX.Y/site-packages` | Global Cache (`~/.nuget/packages`) |
| **Run App** | `node app.js` | `go run main.go` | `python app.py` | `dotnet run` |
| **Build Binary** | `pkg` / `esbuild` | `go build -o app` | `PyInstaller` / `Nuitka` | `dotnet publish -c Release` |
| **Variable Decl.** | `let x = 10;` | `var x int = 10` or `x := 10` | `x = 10` | `int x = 10;` or `var x = 10;` |
| **Constants** | `const Z = 3.14;` | `const Z = 3.14` | `Z: Final = 3.14` | `const double Z = 3.14;` |
| **Null Value** | `null` / `undefined` | `nil` | `None` | `null` |
| **String Interp.** | `` `Hello ${name}` `` | `fmt.Sprintf("Hello %s", name)` | `f"Hello {name}"` | `$"Hello {name}"` |
| **Primitive Types** | `number`, `string`, `boolean` | `int`, `float64`, `string`, `bool` | `int`, `float`, `str`, `bool` | `int`, `double`, `string`, `bool` |
| **Type Assertion** | `val as string` | `str := val.(string)` | `str(val)` / `isinstance()` | `(string)val` / `val as string` |
| **Fixed Array** | `Object.freeze([1, 2])` | `arr := [2]int{1, 2}` | `tpl = (1, 2)` | `int[] arr = [1, 2];` |
| **Dynamic Array** | `list.push(3)` | `slice = append(slice, 3)` | `list.append(3)` | `list.Add(3);` |
| **Iteration** | `arr.forEach((item, index) => ...)` | `for index, item := range slice` | `for index, item in enumerate(list):` | `foreach (var item in list)` |
| **Map/Filter** | `arr.map(...)` / `arr.filter(...)` | Explicit `for` loops | `[f(x) for x in list]` | LINQ `.Select(...)` / `.Where(...)` |
| **Dictionary/Map** | `new Map()` / `{}` | `make(map[string]int)` | `{}` / `dict()` | `new Dictionary<string, int>()` |
| **Key Check** | `'key' in obj` / `map.has('key')` | `val, ok := m["key"]` | `"key" in dict` | `dict.ContainsKey("key")` |
| **If Condition** | `if (x > 5) { ... }` | `if x > 5 { ... }` | `if x > 5:` | `if (x > 5) { ... }` |
| **Init in If** | N/A | `if err := do(); err != nil` | `if (err := do()):` | N/A |
| **Loops** | `for`, `while`, `do-while` | `for` | `for`, `while` | `for`, `foreach`, `while`, `do-while` |
| **Switch/Match** | `switch(x) { case 1: break; }` | `switch x { case 1: ... }` | `match x:` | `switch (x)` / `switch expression` |
| **Error Handling** | `try { ... } catch (err) { ... }` | `res, err := do()` | `try: ... except Exception as err:` | `try { ... } catch (Exception err) { ... }` |
| **Throw Error** | `throw new Error("msg")` | `panic("msg")` | `raise Exception("msg")` | `throw new Exception("msg");` |
| **Cleanup** | `try { ... } finally { ... }` | `defer cleanup()` | `with` / `finally` | `using` / `finally` |
| **Class/Struct** | `class User { ... }` | `type User struct { ... }` | `class User:` | `class User { ... }` / `record User` |
| **Instantiation** | `const u = new User();` | `u := User{ ... }` | `u = User()` | `var u = new User();` |
| **Method Decl.** | `getName() { ... }` | `func (u User) GetName()` | `def get_name(self):` | `public string GetName() { ... }` |
| **Inheritance** | `class Admin extends User` | `type Admin struct { User }` | `class Admin(User):` | `class Admin : User` |
| **Interface** | `interface Reader { ... }` | `type Reader interface { ... }` | `Protocol` / `ABC` | `interface IReader { ... }` |
| **Binding** | `implements Reader` | Implicit | Duck Typing / `Protocol` | `class Doc : IReader` |
| **Access Control** | `public` / `private` / `#field` | Capitalized (`Name`) / Lower (`name`) | `_private` / `__very_private` | `public` / `private` / `protected` |
| **Async Execution**| `async / await` | `go myFunc()` | `async / await` | `async / await` |
| **Async Channels** | `new Promise(...)` | `ch := make(chan int)` | `asyncio.Future()` / `Queue` | `TaskCompletionSource` / `Channel` |
| **Await Result** | `await promise` | `res := <-ch` | `await future` | `await task;` |
| **Concurrency** | Single-threaded Event Loop | `sync.Mutex` | GIL / `threading.Lock` | `lock` / `SemaphoreSlim` |
| **Web Frameworks** | Express, Fastify, NestJS | Gin, Fiber, Echo, `net/http` | FastAPI, Django, Flask | ASP.NET Core Web API |
| **ORM / Database** | Prisma, TypeORM, Mongoose | GORM, Ent, sqlx, pgx | SQLAlchemy, Tortoise, Peewee | Entity Framework Core, Dapper |
| **Validation** | Zod, Joi | go-playground/validator | Pydantic | FluentValidation |
| **Env / Config** | `dotenv` | Viper, godotenv | `python-dotenv`, `pydantic-settings` | `IConfiguration` / `appsettings.json` |
| **Testing** | Jest, Vitest | Native `testing`, testify | PyTest, unittest | xUnit, NUnit, MSTest |