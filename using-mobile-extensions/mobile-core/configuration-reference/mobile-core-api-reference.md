# Mobile Core API Reference

## Track app actions

Actions are events that occur in your app. Use this API to track and measure an action. Each action has one or more corresponding metrics that are incremented each time the event occurs. For example, you might call this API for each new subscription each time an article is viewed, or each time a level is completed.

{% hint style="warning" %}
You must call this API when an event that you want to track, occurs. In addition to the action name, you may send additional context data with each track action call. 
{% endhint %}

{% hint style="info" %}
If you have the **Analytics** extension setup, this method will send an Analytics action tracking hit along with the optional context data you provide.
{% endhint %}

{% tabs %}
{% tab title="Android" %}
#### Java

### trackAction

#### Syntax

```java
public static void trackAction(final String action, final Map<String, String> contextData)
```

#### Example

```java
Map<String, String> additionalContextData = new HashMap<String, String>();
additionalContextData.put("customKey", "value");
MobileCore.trackAction("loginClicked", additionalContextData);
```
{% endtab %}

{% tab title="Objective-C" %}
#### Objective-C

### trackAction

#### Syntax

```objectivec
+ (void) trackAction: (nullable NSString*) action data: (nullable NSDictionary*) data;
```

#### Example

```objectivec
 [ACPCore trackAction:@"action name" data:@{@"key":@"value"}];
```
{% endtab %}

{% tab title="Swift" %}
#### Swift

### trackAction

#### Syntax

```swift
+ (void) trackAction: (nullable NSString*) action data: (nullable NSDictionary*) data;
```

#### Example

```swift
ACPCore.trackAction("action name", data: ["key": "value"])
```
{% endtab %}
{% endtabs %}

## Track app states and views

States represent screens or views in your app. Each time a new state is displayed in your application, for example, when a user navigates from the home page to the news feed, this API may be called.. This method sends an Analytics state tracking hit with optional context data.

{% hint style="info" %}
If you have the **Analytics** extension setup, this API will increment page views and an Analytics state tracking hit along with the optional context data you provide.
{% endhint %}

{% tabs %}
{% tab title="Android" %}
#### Java

 In Android, trackState is typically called each time a new activity is loaded

### trackState <a id="trackstate"></a>

#### **Syntax** <a id="syntax-1"></a>

```text
public static void trackState(final String state, final Map<String, String> contextData)
```

#### Example <a id="example-1"></a>

```text
Map<String, String> additionalContextData = new HashMap<String, String>();         additionalContextData.put("customKey", "value");         MobileCore.trackState("homePage", additionalContextData);
```
{% endtab %}

{% tab title="Objective-C" %}
#### Objective-C

### trackState

#### Syntax

```objectivec
+ (void) trackState: (nullable NSString*) state data: (nullable NSDictionary*) data;
```

#### Example

```objectivec
 [ACPCore trackState:@"state name" data:@{@"key":@"value"}];
```
{% endtab %}

{% tab title="Swift" %}
#### Swift

### trackState

#### Syntax

```objectivec
+ (void) trackState: (nullable NSString*) state data: (nullable NSDictionary*) data;
```

#### Example

```swift
ACPCore.trackState("state name", data: ["key": "value"])
```
{% endtab %}
{% endtabs %}

## Logging

The logging APIs allow log messages to be tagged and filtered with a the Mobile SDK log messages. It allows a separation between Mobile SDK messages and application messages in the device log files. 

As an application developer, use the `setLogLevel` API to filter the log messages coming from the Mobile SDK.

As a Mobile SDK extension developer, use the `log` APIs to include extension log messages with Mobile SDK core log messages.

The Mobile SDK logging modes in order of verbosity from least to most is `ERROR`, `WARNING`, `DEBUG`, and `TRACE`.



{% tabs %}

{% tab title="Android" %}

#### Java

### setLogLevel

#### Syntax

```java
public static void setLogLevel(LoggingMode mode)
```

#### Example

```java
MobileCore.setLogLevel(com.adobe.marketing.mobile.LoggingMode.VERBOSE);
```

{% endtab %}

{% tab title="Objective-C" %}

#### Objective-C

### setLogLevel

#### Syntax

#### Example

{% endtab %}

{% tab title="Swift" %}

#### Swift

### setLogLevel

#### Syntax

#### Example

{% endtab %}

{% endtabs %}



{% tabs %}

{% tab title="Android" %}

#### Java

### getLogLevel

#### Syntax

```java
public static LoggingMode getLogLevel()
```

#### Example

```java
LoggingMode mode = MobileCore.getLogLevel();
```

{% endtab %}

{% tab title="Objective-C" %}

#### Objective-C

### getLogLevel

#### Syntax

#### Example

{% endtab %}

{% tab title="Swift" %}

#### Swift

### getLogLevel

#### Syntax

#### Example

{% endtab %}

{% endtabs %}



{% tabs %}

{% tab title="Android" %}

#### Java

The `MobileCore` logging APIs use the `android.util.Log` APIs to log message to Android.

- `MobileCore.logTrace` calls `android.util.Log.v`
- `MobileCore.logDebug` calls `android.util.Log.d`
- `MobileCore.logWarning` calls `android.util.Log.w`
- `MobileCore.logError` calls `android.util.Log.e`

### log

#### Syntax

```java
public static void logTrace(final String tag, final String message)
public static void logDebug(final String tag, final String message)
public static void logWarning(final String tag, final String message)
public static void logError(final String tag, final String message)
```

#### Example

```java
MobileCore.logDebug("MyActivity", "Debug message.");
```

{% endtab %}

{% tab title="Objective-C" %}

#### Objective-C

### log

#### Syntax

```objective-c
+ (void) logTrace: (nonnull NSString*) source format: (nonnull NSString*) format, ...;

+ (void) logTrace: (nonnull NSString*) source format: (nonnull NSString*) format args: (va_list) args;

+ (void) logDebug: (nonnull NSString*) source format: (nonnull NSString*) format, ...;

+ (void) logDebug: (nonnull NSString*) source format: (nonnull NSString*) format args: (va_list) args;

+ (void) logWarning: (nonnull NSString*) source format: (nonnull NSString*) format, ...;

+ (void) logWarning: (nonnull NSString*) source format: (nonnull NSString*) format args: (va_list) args;

+ (void) logError: (nonnull NSString*) source format: (nonnull NSString*) format, ...;

+ (void) logError: (nonnull NSString*) source format: (nonnull NSString*) format args: (va_list) args;
```

#### Example

```objective-c
[ACPCore logTrace:@"exampleTag", format: @"formatted %@ number %d printed from function: %@", args: getVaList:@{@"text", 2, #function}];
```

{% endtab %}

{% tab title="Swift" %}

#### Swift

### log

#### Syntax

```swift
+ (void) logTrace: (nonnull NSString*) source format: (nonnull NSString*) format, ...;

+ (void) logTrace: (nonnull NSString*) source format: (nonnull NSString*) format args: (va_list) args;

+ (void) logDebug: (nonnull NSString*) source format: (nonnull NSString*) format, ...;

+ (void) logDebug: (nonnull NSString*) source format: (nonnull NSString*) format args: (va_list) args;

+ (void) logWarning: (nonnull NSString*) source format: (nonnull NSString*) format, ...;

+ (void) logWarning: (nonnull NSString*) source format: (nonnull NSString*) format args: (va_list) args;

+ (void) logError: (nonnull NSString*) source format: (nonnull NSString*) format, ...;

+ (void) logError: (nonnull NSString*) source format: (nonnull NSString*) format args: (va_list) args;
```

#### Example

```swift
ACPCore.logTrace("exampleTag", format: "swift formatted %@ number %d printed from function: %@", args: getVaList(["text", 2, #function]));
```

{% endtab %}

{% endtabs %}



## Further Reading

* What is [context data](https://marketing.adobe.com/resources/help/en_US/sc/implement/context_data_variables.html)?

