---
date: 2021-07-27T14:51
---

# Testing pulumi functions that require config in [[golang]]

The `pulumi.WithMocks` does not currently mock the config nor does it read from the provided config. To overcome this it is necessary to create a new `WithMocks` function. Originally from [this](https://github.com/pulumi/pulumi/issues/4472#issuecomment-731012097) GitHub Issue comment.

```go
func WithMocksAndConfig(project, stack string, config map[string]string, mocks pulumi.MockResourceMonitor) pulumi.RunOption {
	return func(info *pulumi.RunInfo) {
		info.Project, info.Stack, info.Mocks, info.Config = project, stack, mocks, config
	}
}
```

And a test function that uses it.

```go
func TestExample(t *testing.T) {
	config := map[string]string{
		"project:example.foo":  "goof",
		"project:example.bar":  "gold",
	}

	err := pulumi.RunErr(func(ctx *pulumi.Context) error {
		rv, err := Example(ctx, "hello, world")
		assert.NoError(t, err)
		assert.NotNil(t, rv)

		return nil
	}, WithMocksAndConfig("project", "stack", config, mocks(0)))
	assert.NoError(t, err)
}
```
