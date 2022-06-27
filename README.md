# Supported Question Types

You can configure the following in questions.yaml:

| Question Type | Description |
|----|----|
| `boolean` | Yields a checkbox component. |
| `string` | Yields a labeled input component for strings. |
| `enum` | Yields a dropdown menu where the items are the values in the enum. |
| `int` | Yields a labeled input component for integers. |
| `float` | Yields a labeled input component for floats. | 
| `labels` and `nodeselectors` | Key-value pair component with a button that allows uploading values from files. |
| `annotations` | Same as the component for labels, except that the value input is a multiline code editor that will visually preserve the spacing when uploading values from files. See screenshot below. |
| `reference_[ANY RESOURCE TYPE]` | When the resource type is specified, the Rancher UI will attempt to fetch every object of that type in the target namespace where the Helm chart will be installed. It will create a dropdown menu where each item in the menu is the name of a resource. The type name is not case sensitive, but the API group must be included if applicable. Examples: `reference_secret`, `reference_configmap`, `reference_apps.deployment`, `reference_storage.k8s.io.storageclass`. |
| `tolerations` | Yields the Tolerations component. See screenshot below. |
| `affinityrules` | Yields the NodeAffinity component. See screenshot below.  |
| `listofstrings` | By default, shows an input. Lets you add and remove inputs for a list of strings of variable length. See screenshot below. |
| `yamlfile` | Component that lets you upload a file and view the result in a code editor with YAML syntax highlighting. See screenshot below. |
| `tmplfile` | Component that lets you upload a file and view the result in a code editor with Go syntax highlighting. See screenshot below. |
| `cloudcredentials` | Yields a dropdown menu of cloud credentials. |

To report a bug or request an enhancement, please open an issue in this repository.

# Screenshots

## String

## Boolean

## Annotations

## Labels

## Node Selectors

## Affinity Rules

## List of Strings

## Reference a Resource

### ConfigMap

### Secret

### Deployment

### Bundle

## Upload YAML File

## Upload .tmpl File

## Cloud Credentials


# Conditional Rendering

Example:

```yaml
- variable: configmap.docker.enabled
  default: true
  description:  Example description of a boolean input
  type: boolean
  label: Docker Runtime
  show_subquestion_if: true
  group: "Container Runtime"
  subquestions:
  - variable: docker.path
    default: "/var/run/docker.sock"
    description: "Docker Runtime Path"
    type: string
    label: Runtime Path
```

# Tabs

Example:

```yaml
- variable: deployment.name
  default: "default name"
  description: Example description of a string input
  type: string
  label: Deployment Name
  group: "Group 2"
- variable: deployment.name
  default: "default name"
  description: Enter node selectors here
  type: nodeselectors
  label: Node Selectors
  group: "Group 2"
```