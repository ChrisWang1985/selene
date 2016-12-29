# Changelog

## 1.0.0 (from master branch)
- new features:
  - automatic driver management (thanks to PR from @SergeyPirogov)
    - including automatic installation of needed drivers via [webdriver_manager](https://github.com/SergeyPirogov/webdriver_manager)
  - object oriented paradigm is now supported in context of webdriver usage
    - Don't like "static" s, ss helpers (from selene.tools module) using global driver instance set by set_driver(...)?
    - now you can use driver.element, driver.all correspondingly
        - where driver = SeleneDriver.wrap(FirefoxDriver()), etc.
        - SeleneDriver has almost the same interface as WebDriver, but with additional methods
          - so you can do everything you can do with raw selenium when needed
- breaking changes:
  - removed out of the box but overcomplicated Widgets support via extending SElement
    - you still can create reusable Widgets in much simpler way
      - see more explanation in [#17](https://github.com/yashaka/selene/issues/17)
  - removed access by config.driver to the driver instance that was set by set_driver(...) from selene.tools
    - it's mandatory to use get_driver(...) from selene.tools for this
  - naming changes:
    - tbd...
- internal
  - improved test coverage
    - added "given-helpers" for preconditions for atomic tests
  - completely refactored implementation to be more structural and solid
    - on the way found non-stable behavior of old implementation and fixed it

## 0.0.8 (released 08.12.2016)
- locked the selenium version to 2.53.1
- fixed encoding issues when working with text of elements in conditions
- added bys.by_name

## 0.0.7 (released 01.03.2016)
- fixed python3 support
- fixed the is_displayed method - now it contains implicit wait for "exist in DOM" instead of "visible"
- added ss(".element", of=Task) syntax in addition to ss(".element").of(Task)
- removed "general interceptor of all unknown methods" SElement's base class (actually commented it in code:)
- refactored lazy inner collection classes to use extend in __init__ and not use SElementsCollectionWrapper (removed the latter and SElementWrapper)
- refactored: removed unnecessary extend from "inner" selement collections (it is needed obviously only for "inner" selement collection element classes)

## 0.0.6 (released 22.02.2016)
- added alias methods:
```
    insist_not = assure_not
    should_not = assure_not
    should_not_be = assure_not
    should_not_have = assure_not
```
- removed stopit from dependencies
- optimized element actions (now they wait for visibility only if first try failed)
  - now selene is as fast as selenium with research of elements before any action. Manual cashing is also available when "raw selenium" speed is needed (semi-automatic customizable cashing will be added later)
- optimized SElementsCollection#find implementation - now it returns first match, not filter everything and then get first among all matches
- mapped all webelement methods to selement (almost all) - now autocompletion works fully for selement
- optimized logic of "inner lazy elements" of collection, removed a bit of magic from it.

## 0.0.5 (released 20.02.2016)

- big refactoring
  - removed currently unstable things
    - automatic driver management (Firefox)
        - so now management is manual but you can use any driver you want (Firefox, Chrome, etc...)
    - screenshooting
  - removed "too complicated" things
    - automatic Loading of widgets
      - so now no any difference between insist, assure, should
  - added aliases (maybe too much... some may be marked as deprecated in future)
    - insist, assure, should, should_be, should_have
    - find more in elements.py, etc.
  - added more overloaded element methods... removed some magic in implementation, still needed to simplify more...
  - added tests, still not enough though
  - added support of other locators (in addition to css)

## 0.0.4
...
## 0.0.3
...
## 0.0.2
...
## 0.0.1
...
