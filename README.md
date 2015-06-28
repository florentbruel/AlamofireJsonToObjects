# AlamofireJsonToObjects

[![Circle CI](https://img.shields.io/circleci/project/evermeer/AlamofireJsonToObjects.svg?style=flat)](https://circleci.com/gh/evermeer/AlamofireJsonToObjects)
[![Issues](https://img.shields.io/github/issues-raw/evermeer/AlamofireJsonToObjects.svg?style=flat)](https://github.com/evermeer/AlamofireJsonToObjects/issues)
[![Stars](https://img.shields.io/github/stars/evermeer/AlamofireJsonToObjects.svg?style=flat)](https://github.com/evermeer/AlamofireJsonToObjects/stargazers)
[![Version](https://img.shields.io/cocoapods/v/AlamofireJsonToObjects.svg?style=flat)](http://cocoadocs.org/docsets/AlamofireJsonToObjects)
[![License](https://img.shields.io/cocoapods/l/AlamofireJsonToObjects.svg?style=flat)](http://cocoadocs.org/docsets/AlamofireJsonToObjects)
[![Platform](https://img.shields.io/cocoapods/p/AlamofireJsonToObjects.svg?style=flat)](http://cocoadocs.org/docsets/AlamofireJsonToObjects)
[![Documentation](https://img.shields.io/badge/documented-100%-brightgreen.svg?style=flat)](http://cocoadocs.org/docsets/AlamofireJsonToObjects)

[![Git](https://img.shields.io/badge/GitHub-evermeer-blue.svg?style=flat)](https://github.com/evermeer)
[![Twitter](https://img.shields.io/badge/twitter-@evermeer-blue.svg?style=flat)](http://twitter.com/evermeer)
[![LinkedIn](https://img.shields.io/badge/linkedin-Edwin Vermeer-blue.svg?style=flat)](http://nl.linkedin.com/in/evermeer/en)
[![Website](https://img.shields.io/badge/website-evict.nl-blue.svg?style=flat)](http://evict.nl)
[![eMail](https://img.shields.io/badge/email-edwin@evict.nl-blue.svg?style=flat)](mailto:edwin@evict.nl?SUBJECT=About EVReflection)

This library was greatly inspired by [AlamofireObjectMapper](https://github.com/tristanhimmelman/AlamofireObjectMapper)

Run the tests to see AlamofireJsonToObjects in action.

## Using AlamofireJsonToObjects in your own App 

'AlamofireJsonToObjects' is now available through the dependency manager [CocoaPods](http://cocoapods.org). 
You do have to use cocoapods version 0.36 or later

You can just add AlamofireJsonToObjects to your workspace by adding the folowing 2 lines to your Podfile:

```
use_frameworks!
pod "AlamofireJsonToObjects"
```

Version 0.36 of cocoapods will make a dynamic framework of all the pods that you use. Because of that it's only supported in iOS 8.0 or later. When using a framework, you also have to add an import at the top of your swift file like this:

```
import AlamofireJsonToObjects
```

If you want support for older versions than iOS 8.0, then you can also just copy the AlamofireJsonToObjects.swift  to your app. 


## Sample code

```
class WeatherResponse: EVObject {
    var location: String?
    var three_day_forecast: [Forecast] = [Forecast]()
}

class Forecast: EVObject {
    var day: String?
    var temperature: NSNumber?
    var conditions: String?
}

class AlamofireJsonToObjectsTests: XCTestCase {
    func testResponseObject() {
        let URL = "https://raw.githubusercontent.com/evermeer/AlamofireJsonToObjects/master/AlamofireJsonToObjectsTests/sample_json"
        Alamofire.request(.GET, URL, parameters: nil)
        .responseObject { (response: WeatherResponse?, error: NSError?) in
            // That was all... You now have a WeatherResponse object with data
        }

        waitForExpectationsWithTimeout(10, handler: { (error: NSError!) -> Void in
            XCTAssertNil(error, "\(error)")
        })
    }
}

```


