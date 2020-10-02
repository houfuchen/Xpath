// about xpath

#### Xpath

https://www.lambdatest.com/blog/complete-guide-for-using-xpath-in-selenium-with-examples/
https://www.edureka.co/community/45639/what-is-xpath-and-what-are-the-types-of-it-selenium-webdriver


XPath known as the XML path is a language that helps to query the XML documents. \
It is used to locate an element on a webpage.

```html
<form method="POST" action="https://accounts.lambdatest.com/register">
<input type="hidden" name="_token" value="W4D7bCygQ4abq2Xa3ckZ2rwG3Wk7f9enPXIIPeuF">
<div class="col-sm-12 google-sign-form"><p class="signup-titel" style="text-align: center;">SIGN UP FOR FREE</p></div> <div class="col-sm-12 google-sign-form">
<input type="text" placeholder="Organization/Company Name" name="organization_name" value="" class="form-control sign-up-input-2 ">
 <input type="text" placeholder="Full Name*" name="name" value="" class="form-control sign-up-input-2 ">
 <input type="email" placeholder="Work Email*" name="email" value="" class="form-control sign-up-input-2 ">
<input type="password" placeholder="Desired Password*" name="password" class="form-control sign-up-input-2 "> <input type="phone" placeholder="Phone*" name="phone" value="" class="form-control sign-up-input-2 "> <p class="terms-cond"><label for="terms_of_service" class="woo">
<input type="checkbox" name="terms_of_service" id="terms_of_service" value="1" class="form-check-input" style="position: relative; margin-left: 0px;"> &nbsp; I agree to the <a target="_blank" href="https://www.lambdatest.com/terms-of-service">Terms of Service</a> and <a target="_blank" href="https://www.lambdatest.com/privacy">Privacy Policy</a></label></p> <button type="submit" class=" btn sign-up-btn-2 btn-block">Signup for Free</button></div>
 <div class="col-sm-12 link-sect"><p class="login-in-link test-left">Already have an account? <a href="/login">Login</a></p></div></form>
```

##### Absolute XPath
&rarr; to find the email input field
`/html/body/div[1]/section/div/div[2]/div/form/div[2]/input[3]`

* created from the root node to the desired element
* starts from a single slash
* disadvantage: very fragile to any changes on the path


##### Relative XPath
&rarr; to find the email input field
`//input[@name='email']`

* created from the middle of the DOM structure
* starts from a double slash
* more compact and easy to use
* less possible to be broken due to changes of the webpage

example:
```Csharp
//Relative xpath for organization field
driver.findElement(By.xpath("//input[@name='organization_name']")).sendKeys("Lambdatest Org");

//Relative xpath for full name field
driver.findElement(By.xpath("//input[@name='name']")).sendKeys("Sadhvi Singh");
```
##### how to write XPath(different types of XPath)
1. `//input[@name='password']`
2. `//a[@href='https://www.lambdatest.com/']`
3. `//*[@id='email_01']`
4. `//input[name='email'][@placeholder='Work Email']`
5. `//input[@type='email' or @name='email']`
6. Dynamics(contains) &rarr; `//input[contains(@class, 'sign-up-input')]`
7. Dynamics(starts with) &rarr; `//input[starts-with(@name, 'organization')]`
8. Text() &rarr; `//button[text()='Signup for Free']`
9. Index &rarr;`//div[@class= 'col-sm-12 google-sign-form']/input[2]`
10. Chained &rarr; `//ul[@class='nav navbar-nav navbar-right']//li[@class='sign-in']`




RBCAUTO
ASSETUSE5

**Explain**:
1. Used `input` tag, `name` attribute, and `password` value.
2. Used `a` tag, `herf` attribute, and `https://www.lambdatest.com/` value.
3. Replaced the `<tag>` with an asterisk `*`, meaning the script will search in the DOM with **any HTML tag that has the `id` attribute with `email_01` value.**
4. With one `input` tag, there were `[name='email'][@placeholder='Work Email']` 2 attributes value pairs used.
5. Locate the element when at least one of the attribute value matches.
6. Usually used when the element is dynamic (part of the attribute values are changing).
```HTML
<input type="text" placeholder="Organization/Company Name" name="organization_name" class="form-control sign-up-input-2 ">
```
For example, the class value might change after each login, so contain method is needed.
7. similar to contain, difference is that the start with can only locate anything that *starts with* the value specified in the method.
8. could find the element with text and tag, can also be used with starts-with and contains
9. when A tag is under B tag, and there are multiple sub-tags like A, then use the index to locate 1 specific sub-tag.
```HTML
<div class="col-sm-12 google-sign-form"><input type="text" placeholder="Organization/Company Name" name="organization_name" value="" class="form-control sign-up-input-2 "> <input type="text" placeholder="Full Name*" name="name" value="" class="form-control sign-up-input-2 "> <input type="email" placeholder="Work Email*" name="email" value="" class="form-control sign-up-input-2 ">
```
10. // parent class -> child class
11.
