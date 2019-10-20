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
