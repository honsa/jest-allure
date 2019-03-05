# Jest-Allure reporting plugin

#### Add more power to your tests using Jest-Allure. Easily generate nice reports at the end of the execution.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)

[![GitHub followers](https://img.shields.io/github/followers/zaqqaz.svg?style=social)](https://github.com/zaqqaz)
[![GitHub stars](https://img.shields.io/github/stars/zaqqaz/jest-allure.svg?style=social)](https://github.com/zaqqaz/jest-allure/stargazers)
[![GitHub watchers](https://img.shields.io/github/watchers/zaqqaz/jest-allure.svg?style=social)](https://github.com/zaqqaz/jest-allure/watchers)
#### Examples
- [Report example](https://103-170502579-gh.circle-artifacts.com/0/Report/Allure/index.html)
- [Visual unit tests with allure report. Demo project](https://github.com/zaqqaz/visual-unit-tests)
- [Simple integration test](https://github.com/zaqqaz/jest-allure/blob/master/examples/__tests__/test1.js)

<hr>

![Allure Report](https://user-images.githubusercontent.com/2823336/40350093-59cad576-5db1-11e8-8210-c4db3bf825a1.png)

[Allure Framework](https://github.com/allure-framework/allure2) is a flexible lightweight multi-language test report tool that not only
shows a very concise representation of what have been tested in a neat web report form,
but allows everyone participating in the development process to extract maximum of useful
information from everyday execution of tests.

#### Installation

```
yarn add -D jest-allure
```
or

```
npm install --save-dev jest-allure
```

#### add reporter to jest.config.js
```
reporters: ["default", "jest-allure"],
```

Run your tests and enjoy 🥤🚀

---

#### How to get a report

To see a report in browser, run in console

```
allure serve
```

If you want to generate html version, run in console

```
allure generate
```

# Advanced features
You can add description, screenshots, steps, severity and lots of other 
fancy stuff to your reports.

Global variable `reporter` available in your tests with such methods:

```
    description(description: string): this;
    severity(severity: Severity): this;
    epic(epic: string): this;
    feature(feature: string): this;
    story(story: string): this;
    startStep(name: string): this;
    endStep(status?: Status): this;
    addArgument(name: string): this;
    addEnvironment(name: string, value: string): this;
    addAttachment(name: string, buffer: any, type: string): this;
    addLabel(name: string, value: string): this;
    addParameter(paramName: string, name: string, value: string): this;
```
**Example**

```
import { Severity } from "jest-allure/dist/Reporter";
import { Feature } from "somwhere in your project";

describe("Fancy test", () => {
        ...
        
        it("Test your amazing feature", async () => {
            reporter
                .description("Feature should work cool")
                .severity(Severity.Critical)
                .feature(Feature.Betting)
                .story("BOND-007");

            reporter.startStep("Check it's fancy");
            // expect that it's fancy
            reporter.endStep();
            
            reporter.startStep("Check it's cool");
            // expect that it's cool
            reporter.endStep();

            const screenshotBuffer = await page.screenshot();
            reporter.addAttachment("Screenshot", screenshotBuffer, "image/png");
        });
        
        ...
    }
);

```
#### What's next

- [x] Generate report from Jest results
- [x] Add steps support
- [x] Add labels support
- [x] Add attachments support
- [x] Add more examples

---

#### Additional projects
[visual-unit-tests](https://github.com/zaqqaz/visual-unit-tests)

[jest-allure-image-snapshot](https://github.com/zaqqaz/jest-allure-image-snapshot)

#### Warning
``jest-allure`` reporter dynamically configure "setupTestFrameworkScriptFile" option in Jest configuration.
**If you have your own setupTestFrameworkScriptFile file**, you need to manually register allure reporter, for it you need to import jest-allure/dist/setup.

```typescript
import "jest-allure/dist/setup";
```

## Contributors
| [<img src="https://avatars3.githubusercontent.com/u/2823336?s=460&v=4" width="100px;"/><br/><sub><b>Denis Artyuhovich</b></sub>](https://denis.by) | [<img src="https://avatars1.githubusercontent.com/u/7804416?s=460&v=4" width="100px;"/><br/><sub><b>Dmitry Bogomya</b></sub>](https://github.com/bogomya) |
| ---      | ---       |
