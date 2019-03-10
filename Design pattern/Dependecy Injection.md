# Dependecy Injection

- Construtor
- Setter
- interface to add setter


### Dagger

- inject cannot be private
- create factory and injector

```java
public class Man {
    @Inject
    public Car car;
    public Man() {
        car = new Car();
    }
    ...
}
```

By adding inject, provide a way to inject car into man
```java
public final class Man_MembersInjector implements MembersInjector<Man> {
  private final Provider<Car> carProvider;

  public Man_MembersInjector(Provider<Car> carProvider) {
    assert carProvider != null;
    this.carProvider = carProvider;
  }

  public static MembersInjector<Man> create(Provider<Car> carProvider) {
    return new Man_MembersInjector(carProvider);
  }

  @Override
  public void injectMembers(Man instance) {
    if (instance == null) {
      throw new NullPointerException("Cannot inject members into a null reference");
    }
    instance.car = carProvider.get();
  }

  public static void injectCar(Man instance, Provider<Car> carProvider) {
    instance.car = carProvider.get();
  }
}
```

- member injected cannot be private: `instance.car = carProvider.get();`

#### Factory
when mark constructor as inject

```java
public final class Car_Factory implements Factory<Car> {
  private static final Car_Factory INSTANCE = new Car_Factory();

  @Override
  public Car get() {
    return new Car();
  }

  public static Factory<Car> create() {
    return INSTANCE;
  }
}
```

When @inject not working in constructor:

1. no constructor
2. 3rd party code
3. constructor needs to be configured

So we need provides

`provide` is similar to injector in constructor, both implementing factory

```java
public final class CarModule_ProvideCarFactory implements Factory<Car> {
  private static final CarModule_ProvideCarFactory INSTANCE = new CarModule_ProvideCarFactory();

  @Override
  public Car get() {
    return Preconditions.checkNotNull(
        CarModule.provideCar(), "Cannot return null from a non-@Nullable @Provides method");
  }

  public static Factory<Car> create() {
    return INSTANCE;
  }

  /** Proxies {@link CarModule#provideCar()}. */
  public static Car proxyProvideCar() {
    return CarModule.provideCar();
  }
}
```

### order

    步骤1：查找Module中是否存在创建该类的方法。
    步骤2：若存在创建类方法，查看该方法是否存在参数
    步骤2.1：若存在参数，则按从步骤1开始依次初始化每个参数
    步骤2.2：若不存在参数，则直接初始化该类实例，一次依赖注入到此结束

    步骤3：若不存在创建类方法，则查找Inject注解的构造函数，看构造函数是否存在参数

    步骤3.1：若存在参数，则从步骤1开始依次初始化每个参数
    步骤3.2：若不存在参数，则直接初始化该类实例，一次依赖注入到此结束


![image](https://upload-images.jianshu.io/upload_images/6193835-760c70f2c486a2e6.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/826)



