# ml-platform

installing using specific version of keycloak allows environment to start

however

airflow dag jobs fail due to start spark cluster jobs failing

```txt
Traceback (most recent call last):
  File "bootstrapper.py", line 430, in <module>
    main()
  File "bootstrapper.py", line 421, in main
    file_op.process_dependencies()
  File "bootstrapper.py", line 96, in process_dependencies
    self.get_file_from_object_storage(archive_file)
  File "bootstrapper.py", line 144, in get_file_from_object_storage
    self.cos_client.fget_object(bucket_name=self.cos_bucket,
  File "/opt/app-root/lib64/python3.8/site-packages/minio/api.py", line 787, in fget_object
    stat = self.stat_object(
  File "/opt/app-root/lib64/python3.8/site-packages/minio/api.py", line 1195, in stat_object
    response = self._url_open(
  File "/opt/app-root/lib64/python3.8/site-packages/minio/api.py", line 2226, in _url_open
    raise ResponseError(response,
minio.error.NoSuchKey: NoSuchKey: message: The specified key does not exist.
Stream closed EOF for ml-workshop/start-spark-cluster.a2d892987c2d40249dcee83e4bb61885 (base)
```

`specified key does not exist` suggests that the task connects to minio but does not find an expected object
