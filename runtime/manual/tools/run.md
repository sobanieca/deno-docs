# `deno run`, run a file

`deno run [OPTIONS] [SCRIPT_ARG]` run a JavaScript or TypeScript file.

## Usage

To run the file at
[https://examples.deno.land/hello-world.ts](https://examples.deno.land/hello-world.ts)
use:

```console
deno run https://examples.deno.land/hello-world.ts
```

You can also run files locally. Ensure that you are in the correct directory and
use:

```console
deno run hello-world.ts
```

By default, all programs are run in sandbox without access to disk, network or
ability to spawn subprocesses because the Deno runtime is
[secure by default](/runtime/manual/runtime/permission_apis). You can grant or deny
required permissions using the [`--allow-*` and `--deny-*` flags](/runtime/manual/basics/permissions).

### Permissions examples

Grant permission to read from disk and listen to network:

```console
deno run --allow-read --allow-net https://deno.land/std/http/file_server.ts
```

Grant permission to read allow-listed files from disk:

```console
deno run --allow-read=/etc https://deno.land/std/http/file_server.ts
```

Grant all permissions (this is not recommended and should only be used for testing):

```console
deno run -A https://deno.land/std/http/file_server.ts
```

## Watch

To watch for file changes and restart process automatically use the `--watch`
flag. Deno's built in application watcher will restart your application as soon
as files are changed. Be sure to put the flag before the file name eg:

```console
deno run --allow-net --watch server.ts
```

Deno's watcher will notify you of changes in the console, and will warn if there
are errors while you work.

## Running a package.json script

Executing scripts with a package.json file can be done with the
[`deno task`](/task_runner) command.

## Running code from stdin

You can pipe code from stdin and run it immediately with:

```console
  curl https://examples.deno.land/hello-world.ts | deno run -
```

## Exiting run

To stop the run command use `ctrl + c`.
