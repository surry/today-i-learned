# Combining Caller-Supplied Arguments and Injected Constructor Arguments with Guice

You can combine caller-supplied arguments and injected constructor arguments with Guice using the @Assisted annotation.

```java
public class RealPayment implements Payment {
    @Inject
   public RealPayment(
      CreditService creditService,
      AuthService authService,
       @Assisted Date startDate,
       @Assisted Money amount) {
     ...
   }
}
```

The injectable arguments are isolated via an intermediate factory object which has methods to create objects of the desired type using the non-injectable arguments. The @Assisted annotation provided by Guice can generate a lot of the boilerplate code needed for these factories, so you just need to write a simple interface for creating your type.

```java
public interface PaymentFactory {
   Payment create(Date startDate, Money amount);
}
```
The factory needs to be configured and bound in a Guice module.

```java
install(new FactoryModuleBuilder()
     .implement(Payment.class, RealPayment.class)
     .build(PaymentFactory.class));
```

Creating an object with @Assisted injections requires injecting the factory and calling the appropriate factory method with the non-injectable arguments.

```java
public class PaymentAction {
    @Inject private PaymentFactory paymentFactory;

   public void doPayment(Money amount) {
     Payment payment = paymentFactory.create(new Date(), amount);
     payment.apply();
   }
}
```

See the Guice [wiki](https://github.com/google/guice/wiki/AssistedInject) and [Javadocs](http://google.github.io/guice/api-docs/latest/javadoc/com/google/inject/assistedinject/FactoryModuleBuilder.html) for more information.
