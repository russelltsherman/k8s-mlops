# Apache Airflow

Airflow is a platform created by the community to programmatically author, schedule and monitor workflows.

## references

[Airflow Documentation](https://airflow.apache.org/docs/)

## issues

airflow pods failed to start 
waiting for migrations 

## notes

using --atomic on helm install prevents the migration job pod from launching
I suspect this is due to the job being triggered by a post-install hook and the post install hook being blocked by --atomic waiting for the install to complete

## Usage

Your release is named airflow.
You can now access your dashboard(s) by executing the following command(s) and visiting the corresponding port at localhost in your browser:

Airflow Webserver:     kubectl port-forward svc/airflow-webserver 8080:8080 --namespace airflow
Default Webserver (Airflow UI) Login credentials:

    username: admin
    password: admin

Default Postgres connection credentials:

    username: postgres
    password: postgres
    port: 5432

You can get Fernet Key value by running the following:

    echo Fernet Key: $(kubectl get secret --namespace airflow airflow-fernet-key -o jsonpath="{.data.fernet-key}" | base64 --decode)

###########################################################

#  WARNING: You should set a static webserver secret key  #

###########################################################

You are using a dynamically generated webserver secret key, which can lead to
unnecessary restarts of your Airflow components.

Information on how to set a static webserver secret key can be found here:
https://airflow.apache.org/docs/helm-chart/stable/production-guide.html#webserver-secret-key
