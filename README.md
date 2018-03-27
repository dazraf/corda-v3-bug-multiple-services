
This reproduces an issue we've seen with Corda v3, whereby a CordaService is started twice per party.

> Please note the CordaService `com.template.MyService`

*To reproduce*

From the IDE run `com.template.NodeDriverKt.main`
In the logs note:

```
[INFO ] 10:52:57,597 [driver-pool-thread-1] (App.kt:82) template.MyService.<init> - Initialising MyService Notary Service {}
[INFO ] 10:52:57,597 [driver-pool-thread-0] (App.kt:82) template.MyService.<init> - Initialising MyService PartyB {}
[INFO ] 10:52:57,599 [driver-pool-thread-1] (App.kt:82) template.MyService.<init> - Initialising MyService Notary Service {}
[INFO ] 10:52:57,601 [driver-pool-thread-0] (App.kt:82) template.MyService.<init> - Initialising MyService PartyB {}
[INFO ] 10:53:02,199 [driver-pool-thread-1] (App.kt:82) template.MyService.<init> - Initialising MyService PartyA {}
[INFO ] 10:53:02,200 [driver-pool-thread-1] (App.kt:82) template.MyService.<init> - Initialising MyService PartyA {}
```