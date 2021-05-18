## The pillars of good unit tests

### Trustworthy

If the test passes you trust it and that the code it tests works for that specific scenario. If the test fails you believe there’s a problem in your code and not in your test.  
A trustworthy test is one that makes you feel you know what’s going on and that you can do something about it.

##### Decide when to remove or change tests

Once you have tests in place, don't change or remove them.

The main reason for removing a test is because it fails for below reason

###### Production bugs

Changes in production code will break existing test, this is an ideal condition. The problem is in the code under test, don't touch the test.

###### Test bugs

If there’s a bug in the test, you need to change the test. Usually hard to detect because tests are assumed to be correct.  
If you implement TDD, less likely to experience this. Because we make the test pass after fail.

What happened to when a test bug is encountered  
1. Denial. The developer will keep looking for a problem in the code itself, changing it, causing all the other tests to start failing.  
2. Amusement. The developer will call another developer, if possible, and they will hunt for the nonexistent bug together.  
3. Debuggerment. The developer will patiently debug the test and discover that there’s a problem in the test.  
4. Acceptance and slappage. The developer will eventually realize where the bug is and will slap their forehead.

What we should do when we encounter a test bug  
1. Fix the bug in your test.  
2. Make sure the test fails when it should. Make (temporary) changes in production code to break the test.  
3. Make sure the test passes when it should. Make changes in production code to make the test pass.

###### Semantics or API changes

There are changes that an object being tested now needs to be used differently, even though it may still have the same end functionality.  
We need to change the test to match the new semantics.

###### Conflicting or invalid tests

The source of conflict is a new feature in production code that’s in direct conflict with a test. Usually there are requirement changes.  
We need to decide which requirement to keep. We should then remove (not comment out) the invalid requirement and its tests.

###### Renaming or refactoring tests

Naming is important! If you encounter a test that has a vague or misleading name or that can be made more maintainable, change the test code (but don’t change the basic functionality of the test)

###### Eliminating duplicate tests

Cons  
1. Harder to maintain different tests that provide the same functionality.  
2. Different quality between test.  
3. Multiple tests may break when a single thing doesn't work.  
4. Those test may have different name.

Pros  
1. Those test may make for a larger and better picture of the object being tested. Because they maybe have some differences.  
2. Some tests may be more expressive than others, so more tests may improve the chances of test readability.

##### Avoid test logic

Each logic introduces a bugs. A test that contains logic is usually testing more than one thing, is less readable and more fragile. A unit test should, as a general rule, be a series of method calls with assert calls, but no control flows, not even try-catch, and with assert calls.  
There are no place for:  
1. switch, if, or else statements  
2. foreach, for, or while loops

##### Test only one concern

If you’re testing more than one thing, giving the test a good name that indicates what’s being tested becomes almost impossible.  
Furthermore, if the first assert fails, it will throw an exception, which means the second assert will never run, and you won’t know if the object behavior differed based on its state.

##### Separate unit from integration tests

If developers don’t trust your tests to run out of the box easily and consistently, they won’t run them.

##### Push for code reviews as much as you push for code coverage

100% code coverage is nothing without code review! Code review + test review (make sure the is good) is a safety net that save us from disaster.

### Maintainable

### Readable

### Naming conventions