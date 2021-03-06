# FX Rate Importer
A low-latent & concurrent importer for FX rates, which provides an abstraction for fetching real-time quotes over REST.

The importer is implemented using Scala's Fututre class to important the rates as quickly as possible, with minimum blocking operations.

The rates are retrieved from the [True FX API](http://www.truefx.com/), which offers free real-time FX quotes for major currency pairs.

## Distribution / Dependency Management

The library is available in the following Nexus repository:

[http://nexus.sharpecapital.co.uk:8081](http://nexus.sharpecapital.co.uk:8081/)

Add this repository to your `pom.xml` file like so:

```xml
<repository>
	<id>sharpe-capital-releases</id>
	<url>http://nexus.sharpecapital.co.uk:8081/content/repositories/releases</url>
</repository>
```

Add this dependency to your `pom.xml` file like so:

```xml
<dependency>
	<groupId>com.sharpe.capital</groupId>
	<artifactId>fx-rate-importer</artifactId>
	<version>0.0.4</version>
</dependency>
```

_(Please check the GitHub repository releases section for the [latest version](https://github.com/sharpecapital/fx-rate-importer/releases))_

## Usage / Examples

#### 1. Fetch Single FX Rate

```scala
import com.sharpe.capital.model.FxRate
import com.sharpe.capital.fetcher.RateFetcher
import com.sharpe.capital.fetcher.TrueFxFetcher

...

val fetcher: RateFetcher = new TrueFxFetcher()

var symbol = "AUD/USD"

var rate: FxRate = fetcher.getRateBySymbol(symbol)
```

#### 2. Fetch Many FX Rates

```scala
import com.sharpe.capital.model.FxRate
import com.sharpe.capital.fetcher.RateFetcher
import com.sharpe.capital.fetcher.TrueFxFetcher

...

val fetcher: RateFetcher = new TrueFxFetcher()

var symbols = Array[String]("AUD/USD", "GBP/USD", "EUR/USD")

var rates: Buffer[FxRate] = fetcher.getRatesBySymbols(symbols)
```

## Contributing

#### BDD Tests
Acceptance tests are written in [ScalaTest](http://www.scalatest.org/). Please add acceptance tests for every new feature or bug fix. You can run the test suite by executing `mvn install`.

#### Documentation
Add documentation for every change. Feel free to send corrections or better docs! 

#### Pull Requests
Send _fixes_ PR on the `master` branch.

## License
MIT © [Sharpe Capital](http://sharpecapital.co.uk)
