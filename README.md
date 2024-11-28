# docker-ecr-buildkite-plugin

This plugin is a custom fork of the [seek-oss/docker-ecr-publish-buildkite-plugin](https://github.com/seek-oss/docker-ecr-publish-buildkite-plugin). It includes enhancements to **allow environment variables to be used as Docker image tags**.

## 🚀 Features

- **Dynamic Tags**: Supports passing environment variables as Docker image tags.
- **Static Tags**: Works seamlessly with static tags as well.
- **Enhanced Validation**: Ensures environment variables are properly handled during execution.

---

## 📦 Installation

To use this plugin, add it to your Buildkite pipeline:

```yaml
steps:
  - plugins:
      - demystdata/docker-ecr#v0.1.0:
          ecr-name: my-repo
          tags:
            - MY_STATIC_TAG          # Static tag
            - MY_EMV_VAR  # Dynamic tag from an environment variable

## ⚠️ Warnings

- **Do NOT use `-` (dash)** in environment variable names used as tags.  
  Bash does not allow dashes in variable names, which will cause runtime errors.  

  Examples:  
  - ✅ Valid: `BUILD_VERSION`  
  - ❌ Invalid: `BUILD-VERSION`  
