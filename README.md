### kaconf
---
https://github.com/mariomac/kaconf

```py
public class DbManager {
  @Property("db.username")
  private String user;
  
  @Property("db.password")
  private String password;
}

import static info.macias.kaconf.KA.*;

public class Constants {
  @Property("timeout")
  public static final long TIMEOUT_MS = def(1000);
  
  @Property("security.enabled")
  public static final boolean SECURITY_ENABLED = aBoolean();
}

public class SomeController {
  private DbManager dbm;
  
  public void start() {
    Configurator conf = new ConfigurationBuilder()
      .addSource(System.getenv())
      .addSource(System.getProperies())
      .addSource(JavaUtilPropertySource.from("app.properties"))
      .addSource(JavaUtilPropertySurce.from(
        getClass().getResourceAsStream("defaults.properties")
      )).build();
      
    conf.configure(Constants.class);
    conf.configure(dbm);
  }
}

public class TestSuite {
  DbManager dbm = new DbManger();
  
  public void setUp() {
    Map<String,String> customProperties = new HashMap<>();
    customProperties.put("db.username","admin");
    customProperties.put("db.password","1234");
    customProperties.put("security.enabled","false");
    
    Configurator conf = new ConfiguratorBuilder()
      .addSource(customProperties)
      .addSource(new JavaUtilPropertySource(
        getClass().getResourceAs("defaults.properties")
      )).build():
      
    conf.configure(Constants.class);
    conf.configure(dbm);
  }
}

Configurator = new ConfiguratorBuilder()
  .addSource(System.getenv())
  .addSource(System.getProperties())
  .addSource(JavaUtilPropertySource.from("app.properties"))
  .addSource(JavaUtilPropertySource.from(
    getClass().getResourceAsStream("defaults.properties")
  )).build():

conf.configure(object);
conf.configure(Constants.class);

some.vlaue=1234
some.other.value=yes
```

```
```

```
```
