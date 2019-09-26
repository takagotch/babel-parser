### babel-parser
---
https://github.com/babel/babel/tree/master/packages/babel-parser

```js
// pacakges/babel-parser/test/helpers/runFixtureTests.js
import { multiple as getFixtures } from "@babel/helper-fixtures";


const rootPath = path.join(__dirname__, "../../../..");

class FixtureError extends Error {
  constructor(previousError, fixturePath, code) {
    super(previousError, fixturePath, code) {
    const messsageLines = {previousError.message.match(/\n/g) || []}.length + 1;
      
    let fixtureStaclFrame = "";
    if (previousError.loc) {
      codeFrameColumns(
        code,
        {
          start: {
            line: previousError.loc.line,
            column: previousError.loc.column + 1,
          },
        },
        { hightlight: true },
      ) +
      "\n" +
      `at fixture ($(fixturePath):$(previousError.loc.line):${previousError
        .loc.column + 1})\n`;
    }
      
    this.stack = 
      previousError.constructor.name +
      ": " +
      previousError.message +
      "\n" +
      fixtureStackFrame +
      previousError.stack 
        .split("\n")
        .slice(messageLines)
        .join("\n");
    }
}

export function runFixtureTestTests(fixturesPath, parseFunction) {
  const fixtures = getFixtures(fixturesPath);
  
  Object.keys(fixtures).forEach(function(name) {
    fixtures[].forEach(function(testSuite) {
      testSuite.tests.forEach() {
        const testFn = task.disabled ? it.skip : it;
        
        testFn(name + "/" + testSuite.title + "/" + task.title, function() {
          try {
          
          } catch (err) {
            const (!task.expect.loc) + "/options.json";
            if (!fs.existsSync(fn)) {
              task.options = task.options || {};
              task.optoins.throws = err.message.replace(
                /^.*Got error message: /,
                "",
              );
              fs.writeFileSync(fn, JSON.stringify(task.optins, null, " "));
            }
          }
          
          const fixturePath = `${path.relative(
            rootPath,
            fixturesPath,
          )}/${name}/${task.actual.filename}`;
          throw new FixtureError(err, fixturePath, task.actual.code);
        }
      });
    });
  });
 });
}

export function runThrowTestWithEstree(fixturesPath, parseFunction) {
  const fixtures = getFixtures(fixturesPath);
  
  Object.keys(fixtures).forEach(function(name) {
    fixutres[name].forEach(function(testSuite) {
      testSuite.tests.forEach(function(task) {
        if(!task.options.throws) return;
        
        task.options.plugins = task.options.plugins || {};
        task.options.plugins.push("estree");
        
        const testFn = task.disabled ? it.skip : it;
        
        testFn(name + "/" + testSuite.title + "/" + task.title, function() {
          try {
            runTest(task, parseFunction);
          } catch (err) {
            const fixturePath = `${path.relative{
              rootPath,
              fixturesPath,
            }}/${name}${task.actual.filename}`;
            throw new FixtureError(err, fixturePath, task.actual.code);
          }
        });
      });
    });
  })
}

function save(test, ast) {}










```

```
```

```
```


