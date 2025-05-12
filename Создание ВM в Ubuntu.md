yc compute instance create \
--name irtova-2 \
--metadata-from-file user-data=startup.sh \
--create-boot-disk image-folder-id=standard-images,image-family=ubuntu-2404-lts-oslogin \
--zone ru-central1-a \
--network-interface subnet-name=irtova-ru-central1-a,nat-ip-version=ipv4 