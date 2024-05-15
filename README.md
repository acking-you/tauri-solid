# Quantum

This template should help get you started developing with Tauri + Solid + TypeScript + TailwindCSS.

> [!Caution]
> Tauri v2 is approaching stability fast, but it not yet considered ready for production use.

## Cloning it 🐑

You can use the Template button on the GitHub UI and shallow clone this repository. Or, do it with degit:

```sh
bunx degit acking-you/tauri-solid
```

Alternatively, good old `git clone` can also work. It's recommended to make a shallow clone so it doesn't bring entire repository history:

```sh
git clone --depth 1 https://github.com/acking-you/tauri-solid
```

## Running 🚤

The snippets below use [bun](https://bun.sh) as the package manager and task runner, but Yarn, NPM, PNPM, or Cargo should also work with the appropriate syntax.

> 🛟 Check the [Tauri Docs](https://beta.tauri.app/) for more guidance on building your app.

First step is always to install JavaScript dependencies from the root:

```sh
bun install
```

## Desktop (MacOS, Linux, or Windows) 🖥️

Once the template is properly cloned, install Node.js dependencies and you can run the Tauri app.

```sh
bun run tauri dev
```

## iOS 🍎

<img src="/docs/ios.png" align="right" height="300"/>

[Check the prerequisites](https://beta.tauri.app/guides/prerequisites/#ios) for having iOS ready to run (MacOS only).
Once that is done, let’s create the XCode project:

```sh
bun run tauri ios init
```

If everything runs successfully (keep an eye for warnings on your terminal).
You can start the development server:

```sh
bun run tauri ios dev --open
```

This command will open XCode with your project, select the simulator and get ready to run.

## Android 🤖

<img src="/docs/android.png" align="right" height="300"/>

[Android Studio and a few other steps will be required](https://beta.tauri.app/guides/prerequisites/#android) to get things up and running.
Once that's done, you can initialize the project:

```sh
bun run tauri android init
```

Open the Android Studio, and run the development build:

```sh
bun run tauri android dev
```

This command will open the Android Pixel simulator.

## Build Optimization ⚡

With a few opinionated defaults, Quantum enforces a smaller binary size than stock Tauri templates. Except for some special cases, these work particularly well.

- `panic = "abort"`
  The compiler will abort the program immediately when a panic occurs in production. Without performing any cleanup. Code will execute faster, the tradeoff is you won't get as much information about the panic when it occurs.

- `codegen-units = 1`
  Explicitly tells the compiler to use only one code generation unit during compilation. Code generation units (CGUs) represent individual units of code that the compiler processes independently.

Reducing CGUs to a minimum will potentially reduces memory consumption and leads to faster compilation time. This setting hinders parallelization, so it's worth to benchmark in your particular app.

- `lto = true`
  Link Time Optimization (lto) enables the compiler to make more aggressive optimizations than it can do at the individual file level, resulting in potentially significant performance improvements in the final executable. However, enabling LTO may increase compilation times and require more memory during the linking phase, as the compiler needs to analyze and optimize a larger amount of code.

- `opt-level = "s"`

Specifying the optimization level to be "size-optimized." This option instructs the compiler to prioritize reducing the size of the generated code while still aiming for reasonable performance.

Using `"s"` is a **balanced** optimization. Some apps may find faster compilation times with `opt-level="z"`, though this may bring slower runtime performance as a tradeoff.

- `strip = true`

Stripping symbols from generated code is generally recommended for release builds where binary size is a concern, and debuggability is less critical. It helps produce leaner binaries, which can be beneficial for deployment, distribution, or running in resource-constrained environments. Additionally, it can slightly enhance security because it makes the binaries harder to analyze.

## Suggested VSCode extensions 💡

- [Tauri](https://marketplace.visualstudio.com/items?itemName=tauri-apps.tauri-vscode)
- [rust-analyzer](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer)
- [Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss)

---

<img width="50" src="/public/tauri.svg" />
