### Modify and resume

Nextflow tracks task executions in a task cache, a key-value store of previously executed tasks. The task cache is used in conjunction with the work directory to recover cached tasks. If you modify and resume your pipeline, only the processes that are changed will be re-executed. The cached results will be used for tasks that don’t change.

## Run a pipeline

The main purpose of the Nextflow CLI is to run Nextflow pipelines with the run command. Nextflow can execute a local script (e.g. ./main.nf) or a remote project (e.g. github.com/nextflow-io/hello).

### Launching a remote project

To launch the execution of a pipeline project, hosted in a remote code repository, you simply need to specify its qualified name or the repository URL after the run command. The qualified name is formed by two parts: the `owner` name and the `repository` name separated by a `/` character.

If a Nextflow project is hosted on GitHub, for example http://github.com/nextflow-io/hello, it can be executed by entering the following command in your shell terminal:

```
nextflow run nextflow-io/hello
```

or using the project URL:

```
nextflow run http://github.com/nextflow-io/hello
```

If the project is found, it will be automatically downloaded to the Nextflow home directory (`$HOME/.nextflow` by default) and cached for subsequent runs.

#### Using a specific revision

Any Git branch, tag, or commit of a project repository can be used when launching a pipeline by specifying the `-r` option:

```
$ nextflow run nextflow-io/hello -r mybranch
```

or

```
$ nextflow run nextflow-io/hello -r v1.1
```

#### Pipeline parameters

Parameters specified on the command line can be also specified in a params file using the `-params-file` option.

```
$ nextflow run main.nf -params-file pipeline_params.yml
```

The -params-file option loads parameters for your Nextflow pipeline from a JSON or YAML file. Parameters defined in the file are equivalent to specifying them directly on the command line. For example, instead of specifying parameters on the command line:

```
$ nextflow run main.nf --alpha 1 --beta two
```

Parameters can be represented in YAML format:

```
alpha: 1
beta: 'two'
```

Or in JSON format:

```
{
  "alpha": 1,
  "beta": "two"
}
```

## Channels
