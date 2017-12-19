### Delivery Archive For AWS Environments.

##### Make the environment to generate delivery zip archives by using this command:
```bash
sudo -u www-data php index.php 'oat\taoDeliveryRdf\scripts\tools\RegisterDeliveryArchive'
```

This command will add a new storage directory (deliveriesArchivesDirectory) where to save the deliveries 
And will subscribe to fallowing event
- DeliveryCreated (it will generate an archive of the delivery after compilation and save the zip)
- DeliveryRemoved (it will remove the zip generated)

##### Revert 
```bash
sudo -u www-data php index.php 'oat\taoDeliveryRdf\scripts\tools\UnRegisterDeliveryArchive'
```

_Note_:
> This command will not remove the archives created.




#### Sync deliveries files (archives). This is available in the context of using the same database but you need to sync the files to other server.
Command availalble 
```bash
sudo -u www-data php index.php 'oat\taoDeliveryRdf\scripts\tools\DeliveryExecutionArchive'
```
```text
 Usage: oat\taoDeliveryRdf\scripts\tools\DeliveryExecutionArchive <mode> [<args>]

Available modes:
   list        get list of all deliveries
   archive     archive all deliveries use --force to force regeneration
   unarchive   unarchive all deliveries --force to force unarchiving
   delete      delete all archives deliveries
```

###### After a zip archive it's unarchived the zip file it's marked as been processed by the env based on php method gethostname() in order to not processed a zip file multiple times by the same env and to be safe using the unarchive command in a while bash block. 
###### In order to ignore the processed flags of zip file use --force flag.