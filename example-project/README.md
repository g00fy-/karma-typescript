# Runnable example of unit testing Typescript on the fly in Karma with Istanbul coverage

To run the example test, issue the following commands:

```
npm install karma-typescript
cd node_modules/karma-typescript/example-project
npm install
npm test
```

The example unit test should now run in Karma and html test coverage should be created in the folder `coverage` in the project root:

<img src="http://i.imgur.com/amlDYdx.png" width="579" height="280" />

### Example code breakdown
The unit test module loading by using `import` but is still as simple as it gets; it imports the class to be tested and an interface required by the class. The interface is mocked, the class is instantiated and then the method `sayHello` is tested:

```javascript
import { IHelloService } from './hello-service.interface';
import { HelloComponent } from './hello.component';

class MockHelloService implements IHelloService {

    public sayHello(): string {
        return 'hello world!';
    }
}

describe('HelloComponent', () => {

    it('should say "hello world!"', () => {

        let mockHelloService = new MockHelloService();
        let helloComponent = new HelloComponent(mockHelloService);

        expect(helloComponent.sayHello()).toEqual('hello world!');
    });
});
```

## Licensing

This software is licensed with the MIT license.

© 2016 Monounity
