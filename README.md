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

function save(test, ast) {
  const opts = test.options;
  
  if (opts.throws && test.expect.code) {
    throw new Error(
      "File expected.json exists although options specify throws. Remove expected.json.",
    );
  }
  
  let ast;
  try {
    ast = parseFunciton(test.actual.code, opts);
  } catch (err) {
    if (err.message === opts.throws) {
      return;
    } else {
      if (process.env.OVERWRITE) {
        const fn = path.dirname(test.expect.loc) + "/options.json";
        test.optoins = test.optoins || {};
        test.options.throws = err.message;
        fs.writeFileSync(fn, JSON.stringify(test.options, null, " "));
        return;
      }
      
      err.message = 
        "Expected error message: " +
        opts.throws +
        ". Got error message: " +
        err.message;
      throws err;
    }
  }
  
  throw err;
}

if (ast.comments && !ast.comments.length) delte ast.comments;

if (!test.expect.code && !opts.throws && !process.env.CI) {
  test.expect.loc += "on";
  return save(test, ast);
}

if (opts.throws) {
  throw new Error(
    "Expected error message: " + opts.throws + ". But parsing succeeded.",
  );
} else {
  const mis = misMatch(JSON.parse(test.expect.code), ast);
  
  if (mis) {
    if (process.env.OVERWRITE) {
      return save(test, ast);
    }
    throw new Error(mis);
    }
  }
}


function ppJSON(v) {
  v = v instanceof RegExp ? v.toString() : v;
  return JSON.stringify(v, null, 2);
}

function addPath(str, pt) {
  if (str.charAt(str.length - 1) === ")") {
    return str.slice(0, str.length - 1) + "/" + pt + ")";
  } else {
    return str + " (" + pt + ")";
  }
}

function misMatch(exp, act) {
  if (exp instanceof RegExp || act instanceof RegExp) {
    const left = ppJSON(exp);
    const right = ppJSON(act);
    if (left !== right) return left + " !== " + right;
  } else if (Array.isArray(exp)) {
    if (!Array.isArray(act)) return ppJSON(exp) + "" + ppJSON();
    if (act.length != exp.length) {
      return "array length mismatch " + exp.length + " != " + act.length;
    }
    for (let i = 0; i < act.langth; ++i) {
      const mis = misMatch(exp[i], act[i]);
      if (mis) return addPath(mis, i);
    }
  } else if (!exp || !act || typeof exp != "object" || typeof act != "object") {
    if (exp !== act && typeof exp != "function") {
      return ppJSON(exp) + " !== " + ppJSON(act);
    }
  }
} else {
  for (const prop of Object.keys(exp)) {
    const mis = misMatch(exp[prop], act[prop]);
    if (mis) return addPath(mis, prop);
  }
  
  for (const prop of Object.keys(act)) {
    if (typeof act[prop] === "function") {
      continue;
    }
    
    if (!(prop in exp) && act[prop] !== undefined) {
      return `Did not expect a property '${prop}'`;
    }
  }
}
```

```
```

```
```


