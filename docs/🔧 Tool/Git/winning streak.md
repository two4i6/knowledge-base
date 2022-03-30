# Project Structure
```shell
$ROOT
├── lib                      
│   ├── news
│   │   └── model # data model and operations for NewItem
│   │       ├── db # database client
│   │       └── fetcher # http fetcher
│   ├── providers # state management
│   ├── screens # screens 
│   ├── utils # utils methods
│   └── widgets # widgets
└── test
```

# Dependencies
``` yaml
hive: ^2.0.6 # key-value database
rxdart: ^0.27.3 # state management
cached_network_image: ^3.2.0 # cache image from network
flutter_html: ^3.0.0-alpha.2 # display news detail
flutter_staggered_animations: ^1.0.0 # animation for grid view
mockito: ^5.1.0 # mock test
```


