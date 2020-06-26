# Kubeflow-Pipeline-Github-Action

Github action to upload and run a Kubeflow pipeline to KubeFlow workspace.

### Inputs
- **kubeflowEndpoint:** Kubeflow API endpoint base URL format http://yourURL/.
- **bearerToken:** Bearer token to of secured Kubeflow API. Read more on how to handle [Creating and storing encrypted secrets](https://help.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets) on Github.  
- **kubeflowPipelineTask:** Input either 'uploadNew' to upload a new pipeline or 'uploadNewVersion' to upload a new pipeline version.
- **pipelineFilePath:** The path compiled pipeline (*.tar.gz). Maximum allowed file size is 32MB.
- **newPipelineName:** Unique name for the new pipeline.
- **existingPipelineName:** Name of existing pipeline when creating new version.
- **versionName:** Unique name for the new pipeline version.
- **pipeline:** Unique name of the Kubeflow pipeline to create run.
- **useDefaultVersion:** If true, this will use the default version of the Kubeflow pipeline provided the pipeline name. Either input 'true' or 'false'.
- **pipelineVersion:** Unique name of the specific pipeline version to be used for creating run.
- **runName:** The name of your new run. Does not have to be unique.
- **pipelineParams:** Kubeflow pipeline parameters in JSON key value format, without the square brackets *{"name":"n1", "value":"v1"}, {"name":"n2", "value":"v2"}*.
- **description:** This input is optional. Provides a description for your run.
- **waitForRunToFinish:** If true, will wait for new run to complete. It will update the status every 15 seconds. Either input 'true' or 'false'.
- **experiment:** Input either 'createNewExperiment' to create a new experiment or 'useExistingExperiment' to use an existing experiment.
- **experimentName:** The name of the experiment you would like your run to use. If the experiment field is set to create a new experiment, this name will need to be unique.
- **experimentDescription:** The optional description of a new experiment. Does not apply to existing experiments.

### Output Variables 
- **kf_pipeline_id:** Id of the pipeline being used to create run.
- **kf_pipeline_version_id:** Id of the pipeline version being used to create run.
- **kf_experiment_id:** Id of the experiment being used.
- **kf_run_id:** Id of the new run.
- **kf_run_status:** The end status of the run. Only available if you choose to wait for the run to complete.