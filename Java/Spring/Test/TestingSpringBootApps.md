# Testing Spring Boot Apps

* JSONAssert is built in.
  * Can do strict or loose comparisons.
* JsonPath
  * Example:

> assetEquals(2,JsonPath.parse(result).read("$.tags.length(), Long.class));

* Can add Awaitility

## @SpringBootTest Isn't always your friend

* Populates the entire ApplicationContext based on the @SpringBootApplications class
* Best suited for integration tests
* Starting your entire application requires access to all dependent infrastructure components.

