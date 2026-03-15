# DEVELOP.md — Quick start from scratch

## Step 0 — Install JDK 21 (JBR recommended)

JetBrains Runtime has DCEVM for enhanced hot-swap (add methods without restart).

1. Download `jbr_jcef-21.*-windows-x64` from https://github.com/JetBrains/JetBrainsRuntime/releases
2. Unzip, e.g. `C:\Components\jbr_jcef-21.0.10-windows-x64-b1163.110`
3. Verify: `C:\Components\jbr_jcef-21.0.10-...\bin\java -version` → should say JBR-21

Regular OpenJDK 21 also works (just no enhanced hot-swap).

## Step 1 — Clone

```bash
git clone --recurse-submodules https://github.com/3ndetz/AUTOCLEF_UPD
cd AUTOCLEF_UPD
```

This pulls 3 submodules: `altoclef`, `Tungsten`, `baritone_altoclef`.

If you forgot `--recurse-submodules`:
```bash
git submodule update --init --recursive
```

## Step 2 — Set JAVA_HOME

```bash
set JAVA_HOME=C:\Components\jbr_jcef-21.0.10-windows-x64-b1163.110
```

Or add to system env vars permanently.

## Step 3 — Build Tungsten

altoclef depends on Tungsten JAR. Build it first:

```bash
cd Tungsten
gradlew.bat build
cd ..
```

Output: `Tungsten/build/libs/tungsten-fabric-ALPHA-1.6.0-1.21compat.jar`

Baritone JAR is pre-built in `baritone_altoclef/maven/` — no action needed.

## Step 4 — Run

```bash
cd altoclef
gradlew.bat :1.21:runClient
```

First run downloads ~1 GB (MC + Fabric + deps). Cached after that.

## Debug with hot-swap

```bash
cd altoclef
gradlew.bat :1.21:runClient --debug-jvm
```

MC starts and waits for debugger on port **5005**.
In VSCode: F5 → "Attach to Minecraft" (config in `.vscode/launch.json`).

With JBR, hot-swap works for method bodies, new methods, and new fields.

## VSCode

Open `AUTOCLEF_UPD.code-workspace` for Gradle panels of both altoclef and Tungsten.

**Note:** `baritone_altoclef` is excluded from Java Language Server indexing — its forge/neoforge subprojects hang the LS. This is intentional.

## Rebuilding Baritone (only if you edit baritone source)

See `Tungsten/DEVELOP.md` Step 1.5 for full instructions.
