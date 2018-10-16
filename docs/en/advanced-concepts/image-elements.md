## Finding and Interacting with Image Elements

Using the experimental `-image` locator strategy, it is possible to send an Appium an image file representing an element you want to tap. If Appium can find a screen region matching your template, it will wrap up information about this region as a standard `WebElement` and send it back to your Appium client.

The strategy will be made available differently for each Appium client, for example: `driver.findElementByImage()`.

### Image Selectors

In conjunction with any locator strategy, you need to use a "selector" which details the specific nature of your find request. In the case of the `-image` strategy, the selector must be a string which is a base64-encoded image file representing the template you want to use for matching.

### Image Elements

If the image match is successful, Appium will cache information about the match and create a standard response for your client to consume, resulting in the instantiation of a standard element object in your test script. Using this element object, you are able to call a small number of methods on the "Image Element", as if it were a bona-fide `WebElement`:

* `click`
* `isDisplayed`
* `getSize`
* `getLocation`
* `getLocationInView`
* `getElementRect`

These actions are supported on "Image Elements" because they are the actions which involve only use of screen position for their functioning. Other actions (like `sendKeys`, for example) are not supported, because all Appium can know based on your template image is whether or not there is a screen region which visually matches it--Appium has no way of turning that information into a driver-specific UI element object, which would be necessary for the use of other actions.
It's important to keep this important point in mind: there is nothing "magic" about Image Elements---they merely reference screen coordinates, and thus "tapping" an Image Element is internally nothing more than Appium constructing a tap at a point in the center of the Image Element's screen bounds.

### Related Settings

