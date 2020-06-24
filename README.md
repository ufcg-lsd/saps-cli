# SAPS CLI

## get-all-tasks

### How to use

```bash
bash get-all-tasks <user-email> <user-password> <dispatcher-address>
```

### Result

```
taskid dataset region inputgatheringtag inputpreprocessingtag algorithmexecutiontag state creationtime updatetime
45b1a50e-2d2d-4f23-8fe8-33fbdbfbbe0c landsat_7 215065 nop-fake-files nop-fake-files nop-fake-files archived 2020-06-12 17:02:29.214 2020-06-12 17:05:16.900263
14eddcac-c400-47d2-b6ba-f092c4ec3ea6 landsat_8 215065 nop-fake-files nop-fake-files nop-fake-files archived 2020-06-12 17:02:29.18 2020-06-12 17:05:17.152581
5daac8e1-8bfe-41e5-a16c-60c9a76ecea7 landsat_8 215065 nop-fake-files nop-fake-files nop-fake-files archived 2020-06-23 14:39:22.061 2020-06-23 14:46:38.40799
6099f40e-2c27-44b6-96df-0f3600e2dd1c landsat_8 215065 nop-download-files nop-download-files nop-download-files archived 2020-06-22 18:58:54.975 2020-06-22 19:12:33.534905
d3bef34f-dddf-49bb-a680-e2ff5e890e5f landsat_7 215065 endtoend-test endtoend-test endtoend-test failed 2020-06-22 19:19:31.378 2020-06-22 19:23:52.893338
70c353e4-d3e0-4f3e-bf8a-ab5779282b31 landsat_7 215065 nop-download-files nop-download-files nop-download-files archived 2020-06-22 18:58:55.003 2020-06-22 19:17:08.70385
```

## get-task-by-id

### How to use

```bash
bash get-task-by-id <user-email> <user-password> <task-id> <dispatcher-address>
```

### Result

```json
{
  "taskId": "45b1a50e-2d2d-4f23-8fe8-33fbdbfbbe0c",
  "dataset": "landsat_7",
  "region": "215065",
  "imageDate": "Jun 23, 2015",
  "state": "ARCHIVED",
  "arrebolJobId": "-1",
  "federationMember": "None",
  "user": "admin@admin.com",
  "priority": 0,
  "inputdownloadingTag": "nop-fake-files",
  "digestInputdownloading": "sha256:8a0431bfec753de2c2ebdcbf557ecbd3488c81cb83140587bbd2801cef05317b",
  "preprocessingTag": "nop-fake-files",
  "digestPreprocessing": "sha256:bc99e10172a1bb25d4cf1a0408636b1dff067137f072507a453f1d88d8bbe672",
  "processingTag": "nop-fake-files",
  "digestProcessing": "sha256:4d28c22c949527519c6841fb104c7e5f073608ce9934f9b06d169f67868cad33",
  "creationTime": "Jun 12, 2020 5:02:29 PM",
  "updateTime": "Jun 12, 2020 5:05:16 PM",
  "status": "NE",
  "error": "available"
}
```

## get-task-links

### How to use

```bash
bash get-task-links <user-email> <user-password> <task-id> <dispatcher-address>
```

### Result

```json
[
  {
    "name": "inputdownloading/215065.tif",
    "url": "https://cloud5.lsd.ufcg.edu.br:8080/swift/v1/saps-systemtest/archiver/70c353e4-d3e0-4f3e-bf8a-ab5779282b31/inputdownloading/215065.tif?temp_url_sig=e3fea810419f32f402c9e4079ded45dfd4ccff1e&temp_url_expires=9223372036854775807&filename=215065.tif"
  },
  {
    "name": "inputdownloading/LC08_L1TP_215065_20150623_20170407_01_T1_B1.TIF",
    "url": "https://cloud5.lsd.ufcg.edu.br:8080/swift/v1/saps-systemtest/archiver/70c353e4-d3e0-4f3e-bf8a-ab5779282b31/inputdownloading/LC08_L1TP_215065_20150623_20170407_01_T1_B1.TIF?temp_url_sig=e6b8fae0b4d5c2c4806187f29fc7750f8cf54b24&temp_url_expires=9223372036854775807&filename=LC08_L1TP_215065_20150623_20170407_01_T1_B1.TIF"
  },
  {
    "name": "inputdownloading/LC08_L1TP_215065_20150623_20170407_01_T1_B10.TIF",
    "url": "https://cloud5.lsd.ufcg.edu.br:8080/swift/v1/saps-systemtest/archiver/70c353e4-d3e0-4f3e-bf8a-ab5779282b31/inputdownloading/LC08_L1TP_215065_20150623_20170407_01_T1_B10.TIF?temp_url_sig=58fc8a225a0f0dc2378b5db4d353d3a2cbafbc11&temp_url_expires=9223372036854775807&filename=LC08_L1TP_215065_20150623_20170407_01_T1_B10.TIF"
  },
  {
    "name": "inputdownloading/LC08_L1TP_215065_20150623_20170407_01_T1_B11.TIF",
    "url": "https://cloud5.lsd.ufcg.edu.br:8080/swift/v1/saps-systemtest/archiver/70c353e4-d3e0-4f3e-bf8a-ab5779282b31/inputdownloading/LC08_L1TP_215065_20150623_20170407_01_T1_B11.TIF?temp_url_sig=ac846d1353efb051b294a90b35d8b20236d7828c&temp_url_expires=9223372036854775807&filename=LC08_L1TP_215065_20150623_20170407_01_T1_B11.TIF"
  },
  ...
]
```

## submit-task

### How to use

```bash
bash submit-task <user-email> <user-password> <lower-left-latitude> <upper-right-latitude> <lower-left-longitude> <upper-right-longitude> <processing-init-date> <processing-final-date> <inputdownloading-tag> <preprocessing-tag> <processing-tag> <dispatcher-address>
```

### Result

```json
[
  "<task-id-01>",
  "<task-id-02>",
  ...
]

```
