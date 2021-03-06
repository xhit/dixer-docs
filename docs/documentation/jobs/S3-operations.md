# S3 operations

Dixer provides a way to do Amazon S3 operations like download or upload a file, etc...

To do this, set the job with type `s3operation`.

The key `bucket` or `bucket_var` should be filled with the target bucket to do the task.

This job type has a key to define the file operation. The key is `operation` and accepts this values:

- `uploadfile`: Upload a file.
- `uploaddir`: Upload a directory.
- `downloadfile`: Download a file.
- `deletefile`: Delete a remote file.
- `deletedir`: Delete a remote directory.
- `downloaddir`: Download a remote directory.

For some operations, keys are differents.

!!! warning
    In Dixer v1.4.0 and below, `local_file_path` is `local_filepath` and `remote_file_path` is `remote_filepath`.

## `uploadfile` and `downloadfile` operations

- `local_file_path`: optional. The local file path to upload/download. String.
- `local_file_path_var`: optional. Variable with the local file path. String.
- `remote_file_path`: optional. The remote file path. String.
- `remote_file_path_var`: optional. Variable with the remote file path. String.

Example:

```toml
[[jobs]]
id = 'file_uploading'
name = 'S3 Upload'
type = 's3operation'
operation = 'uploadfile'
ignore_error = false
disable = false
connection_id = 'aws-connection'
bucket = 'bucketid'
local_file_path = 'test/file.xlsx'
remote_file_path = 'data/fileuploaded.xlsx'
local_file_path_var = ''
remote_file_path_var = ''
```

Example to download:

```toml
[[jobs]]
id = 'file_downloading'
name = 'S3 Download'
type = 's3operation'
operation = 'downloadfile'
ignore_error = false
disable = false
connection_id = 'aws-connection'
bucket = 'bucketid'
local_file_path = 'test/filedownloaded.xlsx'
remote_file_path = 'data/file.xlsx'
local_file_path_var = ''
remote_file_path_var = ''
```

## `deletefile` operation

- `remote_file_path`: optional. The remote file path. String.
- `remote_file_path_var`: optional. Variable with the remote file path. String.

Example:

```toml
[[jobs]]
id = 'file_delete'
name = 'S3 Delete file'
type = 's3operation'
operation = 'deletefile'
ignore_error = false
disable = false
connection_id = 'aws-conn'
bucket = 'bucketid'
remote_file_path = 'data/file.xlsx'
remote_file_path_var = ''
```

!!! tip
    You can delete an empty directory with this operation adding backslash at the end of the directory.


## `uploaddir` operation

- `local_directory`: optional. The local directory. String.
- `local_directory_var`: optional. Variable with the local directory. String.

```toml
[[jobs]]
id = 'dir_upload'
name = 'S3 Upload directory'
type = 's3operation'
operation = 'uploaddir'
ignore_error = false
disable = false
connection_id = 'aws-connection'
bucket = 'bucketid'
local_directory = "Path of local directory"
```

## `deletedir` operation keys

- `remote_directory`: optional. The remote directory. String.
- `remote_directory_var`: optional. Variable with the remote directory. String.

```toml
[[jobs]]
id = 'dir_delete'
name = 'S3 Delete directory'
type = 's3operation'
operation = 'deletedir'
ignore_error = false
disable = false
connection_id = 'aws-connection'
bucket = 'bucketid'
remote_directory = 'data/'
remote_directory_var = ''
```

## `downloaddir` operation keys

- `remote_directory`: optional. The remote directory. String.
- `remote_directory_var`: optional. Variable with the remote directory. String.
- `local_directory`: optional. The local directory. String.
- `local_directory_var`: optional. Variable with the local directory. String.

```toml
[[jobs]]
id = 'dir_download'
name = 'S3 Download directory'
type = 's3operation'
operation = 'downloaddir'
connection_id = 'aws-connection'
bucket = 'bucketid'
remote_directory = 'data/'
local_directory = "Path of local directory"
```