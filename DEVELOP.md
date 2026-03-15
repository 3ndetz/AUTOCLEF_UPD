# DEVELOP.md — Dev environment setup

## JDK: JetBrains Runtime (JBR) with DCEVM

We use **JBR 21** instead of regular OpenJDK — it supports enhanced hot-swap (add methods/fields without restart).

1. Download `jbr_jcef-21.*-windows-x64` from https://github.com/JetBrains/JetBrainsRuntime/releases
2. Unzip to e.g. `C:\Components\jbr_jcef-21.0.10-windows-x64-b1163.110`
3. Set before running Gradle:
   ```bash
   set JAVA_HOME=C:\Components\jbr_jcef-21.0.10-windows-x64-b1163.110
   ```

## Clone (first time)

```bash
git clone --recurse-submodules https://github.com/3ndetz/AUTOCLEF_UPD
```

Submodules: `altoclef`, `Tungsten`, `baritone_altoclef`.

## Build & run altoclef (1.21)

```bash
cd altoclef
gradlew.bat :1.21:runClient
```

First build needs Tungsten JAR. Build it first if missing:

```bash
cd Tungsten
gradlew.bat build
```

JAR: `Tungsten/build/libs/tungsten-fabric-ALPHA-1.6.0-1.21compat.jar`

## Debug with hot-swap

```bash
cd altoclef
gradlew.bat :1.21:runClient --debug-jvm
```

MC waits for debugger on port **5005**. Attach via VSCode (F5 → "Attach to Minecraft").

## VSCode workspace

Open `AUTOCLEF_UPD.code-workspace` — shows Gradle panels for both altoclef and Tungsten.

`baritone_altoclef` is excluded from Java indexing (its forge/neoforge subprojects hang the Language Server).

## Baritone

Pre-built JAR in `baritone_altoclef/maven/`. Only rebuild if you change baritone source — see `Tungsten/DEVELOP.md` for details.
