# Tauri + Vue 3

This template should help get you started developing with Tauri + Vue 3 in Vite. The template uses Vue
3 `<script setup>` SFCs, check out
the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

## Project creation steps

### 1. Install commands with cargo

```shell
cargo install create-tauri-app
cargo install tauri-cli
```

### 2. Project init with cargo

```shell
cargo create-tauri-app
```

## Clion IDE Debugging Setup

### 1. Start Development Server

```shell
npm run dev
```

### 2. Start and Debug App with  `fn main()` in `\src-tauri\src\main.rs`

## VSCode IDE Debugging Setup

### 1. Add `launch.json` to `.vscode` directory

```json
{
  // Use IntelliSense to learn about possible attributes.
  // Hover to view descriptions of existing attributes.
  // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
  "version": "0.2.0",
  "configurations": [
    {
      "type": "lldb",
      "request": "launch",
      "name": "Tauri Development Debug",
      "cargo": {
        "args": [
          "build",
          "--manifest-path=./src-tauri/Cargo.toml",
          "--no-default-features"
        ]
      },
      // task for the `beforeDevCommand` if used, must be configured in `.vscode/tasks.json`
      "preLaunchTask": "ui:dev"
    },
    {
      "type": "lldb",
      "request": "launch",
      "name": "Tauri Production Debug",
      "cargo": {
        "args": [
          "build",
          "--release",
          "--manifest-path=./src-tauri/Cargo.toml"
        ]
      },
      // task for the `beforeBuildCommand` if used, must be configured in `.vscode/tasks.json`
      "preLaunchTask": "ui:build"
    }
  ]
}
```

### 2. Add `tasks.json` to `.vscode` Directory

```json
{
  // See https://go.microsoft.com/fwlink/?LinkId=733558
  // for the documentation about the tasks.json format
  "version": "2.0.0",
  "tasks": [
    {
      "label": "ui:dev",
      "type": "shell",
      // `dev` keeps running in the background
      // ideally you should also configure a `problemMatcher`
      // see https://code.visualstudio.com/docs/editor/tasks#_can-a-background-task-be-used-as-a-prelaunchtask-in-launchjson
      "isBackground": true,
      // change this to your `beforeDevCommand`:
      "command": "npm",
      "args": [
        "dev"
      ]
    },
    {
      "label": "ui:build",
      "type": "shell",
      // change this to your `beforeBuildCommand`:
      "command": "npm",
      "args": [
        "build"
      ]
    }
  ]
}
```

### 3. Start Development Server

```shell
npm run dev
```

### 4. Start and Debug App With  `fn main()` in `\src-tauri\src\main.rs`