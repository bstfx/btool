# Project Structure Guide for Houdini Loader Tool

This document explains the required project folder structure and naming conventions to use the Houdini Shelf Loader Tool effectively across any project.

---

## Work Folder (WIP)

**Path Format:**

```
<drive>/<client_folder>/<project_name>/<sequence>/<shot>/work/<department>/
```

**Example:**

```
D:/client_local/projbtool/BST/sh050/work/anim/
```

- Each department folder (e.g. `anim`, `fx`, `layout`) is created automatically when you select a department through the tool UI.

---

## Release Folder (Final Output)

**Path Format:**

```
<drive>/<client_folder>/<project_name>/<sequence>/<shot>/release/<department>/<cacheType>/
```

Where `<cacheType>` can be:

- `cameraCache`
- `geoCache`
- (additional types such as `fxCache`, etc.)

---

## Camera Cache File Format

```
<sequence>_<shot>_<department>_v<version>_camera.abc
```

**Example:**

```
D:/client_local/projbtool/BST/sh050/release/anim/cameraCache/bst_sh50_anim_v001_camera.abc
```

---

## Geo Cache File Format

```
<sequence>_<shot>_<assetName>_v<version>_<department>cache.abc
```

**Example:**

```
D:/client_local/projbtool/BST/sh050/release/anim/geoCache/bst_sh050_bunny_v001_animcache.abc
```

---

## Naming Requirements (Strict)

- **Camera cache:** Must follow: `dept_version_camera.abc`
  - Example: `anim_v001_camera.abc`
- **Geo cache:** Must include asset name: `name_version_animcache.abc`
  - Example: `bunny_v001_animcache.abc`

These patterns are mandatory for proper detection and loading in Houdini via the loader.

---

## Tool Behavior

- Cache metadata is temporarily saved to your system's local `%temp%` Houdini folder.
- To change the snippet temporary path, locate **line 1049** in the `btool.shelf` file and edit it manually.
- You can also adjust other settings such as paths, behavior, or versioning logic within the same file.

---

## Example Directory Tree

```
D:/
└── client_local/
    └── projbtool/
        └── BST/
            └── sh050/
                ├── work/
                │   ├── anim/
                │   ├── fx/
                │   └── layout/
                └── release/
                    └── anim/
                        ├── cameraCache/
                        │   └── bst_sh50_anim_v001_camera.abc
                        └── geoCache/
                            └── bst_sh050_bunny_v001_animcache.abc
```

---

Keep this structure consistent across your team to ensure seamless integration with Houdini loading tools and project automation systems.

