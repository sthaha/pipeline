# An experiment with Tekton Pipeline for Voting App

## Application Design

The voting app has a backend/[api] and a frontend/[ui]. The [api] is
written in go and the [ui] uses python - flask.

See also:
  - [API repo][api]
  - [UI repo][ui]

## Pipeline
The pipeline build both apps in parallel, deploys [api] then the [ui] app.

```
  (build-api) ---> (deploy-api)
                               \
  (build-ui) -------------------`-> (deploy-ui)

```

[api]: http://github.com/sthaha/vote-api
[ui]: http://github.com/sthaha/vote-ui

## Running

```
./pipeline setup
./pipeline run
```



## Explanation

` ./pipeline setup ` command performs the following

1. validates that `oc` and `tkn` are installed
1. create a `$NAMESPACE` (default: voting)
1. sets up required tasks from openshift and tekton catalogs (oc, s2i-python-3,
    s2i-go)
1. applies `resources/` directory which contains `api` and `ui` git and image
   pipeline-resource definitions (manifests)
1. applies the `pipeline.yaml`

`./pipeline run` runs the pipeline and shows the log
