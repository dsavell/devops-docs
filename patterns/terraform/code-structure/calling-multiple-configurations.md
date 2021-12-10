# Calling - Multiple Configurations

The multiple configurations setup is useful for organizations or enterprises that has infrastructure that is not necassaily the same in each environment.

You could have the concept that you wish to centrally controll network resources, logging resources, security resources, those resources may not necassarily be the same for each environment.

The bellow pattern will make some assumption however the princpal / concept should ideally be the same however you want to isolate you environment.

* Azure
  * Multiple subscriptions.
* Google Cloud Platform
  * Multiple projects.
* AWS
  * Multiple accounts.
