# datastore-metadata
All the LIS Datastore YAML files (and some others we consider "metadata") under one roof.

This repository contains the description_[Genus]_[species].yml and README.[collection].yml files in the LIS Datastore as well as some other files handled as metadata.

Several types of files should be checked for valid format and contents prior to pushing to the datastore-metadata repository:

```
  validate.sh description_genus_species YAML_FILE
  validate.sh description_genus         YAML_FILE
  validate.sh readme                    YAML_FILE
```

Each collection, also contains a CHECKSUM.[collection].md5 file (mainly because this can be used as a list of the datas files in the collection); these should be generated with the script [mdsum-folder.bash](https://github.com/legumeinfo/datastore-specifications/blob/main/scripts/mdsum-folder.bash)

After creating a new collection in the datastore (or making changes to the contents of an existing collection, which should be followed by validation as described above and an update to the CHECKSUM.[collection].md5), please be sure to:

```
git add README.[collection].yml CHECKSUM.[collection].md5
git commit (with some informative log message)
git push
```

All other files are blocked from being added to the repository in .gitignore -- except files that probably shouldn't belong in the Datastore to begin with.
Having these files up-to-date in the github repo is important not only for version control purposes, but also because some of our tools operate by cloning this repo and using the metadata as a light-weight representation of the state of the datastore. Some files (e.g. BUSCO summary files) have also been introduced into this repository to facilitate consumption by applications from a cloned version of the repository.

GitHub Actions will now validate your file(s) upon commit and will fail if they don't pass validation, although this is only apparent from the github UI (https://github.com/legumeinfo/datastore-metadata/actions) and leaves the files in the datastore proper still needing to be fixed.

For additional description of protocols related to data curation for the data store, see https://github.com/legumeinfo/datastore-specifications/tree/main/PROTOCOLS

