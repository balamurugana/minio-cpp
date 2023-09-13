add_executable(MakeBucket MakeBucket.cc)
target_link_libraries(MakeBucket miniocpp ${requiredlibs})

add_executable(RemoveBucket RemoveBucket.cc)
target_link_libraries(RemoveBucket miniocpp ${requiredlibs})

add_executable(BucketExists BucketExists.cc)
target_link_libraries(BucketExists miniocpp ${requiredlibs})

add_executable(ListBuckets ListBuckets.cc)
target_link_libraries(ListBuckets miniocpp ${requiredlibs})

add_executable(StatObject StatObject.cc)
target_link_libraries(StatObject miniocpp ${requiredlibs})

add_executable(RemoveObject RemoveObject.cc)
target_link_libraries(RemoveObject miniocpp ${requiredlibs})

add_executable(DownloadObject DownloadObject.cc)
target_link_libraries(DownloadObject miniocpp ${requiredlibs})

add_executable(UploadObject UploadObject.cc)
target_link_libraries(UploadObject miniocpp ${requiredlibs})

add_executable(GetObject GetObject.cc)
target_link_libraries(GetObject miniocpp ${requiredlibs})

add_executable(ListObjects ListObjects.cc)
target_link_libraries(ListObjects miniocpp ${requiredlibs})

add_executable(PutObject PutObject.cc)
target_link_libraries(PutObject miniocpp ${requiredlibs})

add_executable(CopyObject CopyObject.cc)
target_link_libraries(CopyObject miniocpp ${requiredlibs})

add_executable(ComposeObject ComposeObject.cc)
target_link_libraries(ComposeObject miniocpp ${requiredlibs})

add_executable(RemoveObjects RemoveObjects.cc)
target_link_libraries(RemoveObjects miniocpp ${requiredlibs})

add_executable(SelectObjectContent SelectObjectContent.cc)
target_link_libraries(SelectObjectContent miniocpp ${requiredlibs})

add_executable(ListenBucketNotification ListenBucketNotification.cc)
target_link_libraries(ListenBucketNotification miniocpp ${requiredlibs})

add_executable(DeleteBucketPolicy DeleteBucketPolicy.cc)
target_link_libraries(DeleteBucketPolicy miniocpp ${requiredlibs})

add_executable(GetBucketPolicy GetBucketPolicy.cc)
target_link_libraries(GetBucketPolicy miniocpp ${requiredlibs})

add_executable(SetBucketPolicy SetBucketPolicy.cc)
target_link_libraries(SetBucketPolicy miniocpp ${requiredlibs})

add_executable(DeleteBucketNotification DeleteBucketNotification.cc)
target_link_libraries(DeleteBucketNotification miniocpp ${requiredlibs})

add_executable(GetBucketNotification GetBucketNotification.cc)
target_link_libraries(GetBucketNotification miniocpp ${requiredlibs})

add_executable(SetBucketNotification SetBucketNotification.cc)
target_link_libraries(SetBucketNotification miniocpp ${requiredlibs})

add_executable(DeleteBucketEncryption DeleteBucketEncryption.cc)
target_link_libraries(DeleteBucketEncryption miniocpp ${requiredlibs})

add_executable(GetBucketEncryption GetBucketEncryption.cc)
target_link_libraries(GetBucketEncryption miniocpp ${requiredlibs})

add_executable(SetBucketEncryption SetBucketEncryption.cc)
target_link_libraries(SetBucketEncryption miniocpp ${requiredlibs})

add_executable(GetBucketVersioning GetBucketVersioning.cc)
target_link_libraries(GetBucketVersioning miniocpp ${requiredlibs})

add_executable(SetBucketVersioning SetBucketVersioning.cc)
target_link_libraries(SetBucketVersioning miniocpp ${requiredlibs})

add_executable(DeleteBucketReplication DeleteBucketReplication.cc)
target_link_libraries(DeleteBucketReplication miniocpp ${requiredlibs})

add_executable(GetBucketReplication GetBucketReplication.cc)
target_link_libraries(GetBucketReplication miniocpp ${requiredlibs})

add_executable(SetBucketReplication SetBucketReplication.cc)
target_link_libraries(SetBucketReplication miniocpp ${requiredlibs})

add_executable(DeleteBucketLifecycle DeleteBucketLifecycle.cc)
target_link_libraries(DeleteBucketLifecycle miniocpp ${requiredlibs})

add_executable(GetBucketLifecycle GetBucketLifecycle.cc)
target_link_libraries(GetBucketLifecycle miniocpp ${requiredlibs})

add_executable(SetBucketLifecycle SetBucketLifecycle.cc)
target_link_libraries(SetBucketLifecycle miniocpp ${requiredlibs})

add_executable(DeleteBucketTags DeleteBucketTags.cc)
target_link_libraries(DeleteBucketTags miniocpp ${requiredlibs})

add_executable(GetBucketTags GetBucketTags.cc)
target_link_libraries(GetBucketTags miniocpp ${requiredlibs})

add_executable(SetBucketTags SetBucketTags.cc)
target_link_libraries(SetBucketTags miniocpp ${requiredlibs})

add_executable(DeleteObjectLockConfig DeleteObjectLockConfig.cc)
target_link_libraries(DeleteObjectLockConfig miniocpp ${requiredlibs})

add_executable(GetObjectLockConfig GetObjectLockConfig.cc)
target_link_libraries(GetObjectLockConfig miniocpp ${requiredlibs})

add_executable(SetObjectLockConfig SetObjectLockConfig.cc)
target_link_libraries(SetObjectLockConfig miniocpp ${requiredlibs})

add_executable(DeleteObjectTags DeleteObjectTags.cc)
target_link_libraries(DeleteObjectTags miniocpp ${requiredlibs})

add_executable(GetObjectTags GetObjectTags.cc)
target_link_libraries(GetObjectTags miniocpp ${requiredlibs})

add_executable(SetObjectTags SetObjectTags.cc)
target_link_libraries(SetObjectTags miniocpp ${requiredlibs})

add_executable(DisableObjectLegalHold DisableObjectLegalHold.cc)
target_link_libraries(DisableObjectLegalHold miniocpp ${requiredlibs})

add_executable(EnableObjectLegalHold EnableObjectLegalHold.cc)
target_link_libraries(EnableObjectLegalHold miniocpp ${requiredlibs})

add_executable(IsObjectLegalHoldEnabled IsObjectLegalHoldEnabled.cc)
target_link_libraries(IsObjectLegalHoldEnabled miniocpp ${requiredlibs})

add_executable(GetObjectRetention GetObjectRetention.cc)
target_link_libraries(GetObjectRetention miniocpp ${requiredlibs})

add_executable(SetObjectRetention SetObjectRetention.cc)
target_link_libraries(SetObjectRetention miniocpp ${requiredlibs})

add_executable(GetPresignedObjectUrl GetPresignedObjectUrl.cc)
target_link_libraries(GetPresignedObjectUrl miniocpp ${requiredlibs})

add_executable(GetPresignedPostFormData GetPresignedPostFormData.cc)
target_link_libraries(GetPresignedPostFormData miniocpp ${requiredlibs})

add_executable(PutObjectProgress PutObjectProgress.cc)
target_link_libraries(PutObjectProgress miniocpp ${requiredlibs})

add_executable(GetObjectProgress GetObjectProgress.cc)
target_link_libraries(GetObjectProgress miniocpp ${requiredlibs})
