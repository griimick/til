# Object vs Map


| Object | Map |
|--------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Keys can be simple data types <br>i.e. integer or string or<br>symbol which are further<br>converted to string. | Keys can be of any type.<br>Arrays and Objects are also<br>accepted as keys. Key types<br>are preserved. |
| original order of elements (pairs)<br>is not preserved. | Order of elements (pairs)<br>is preserved. |
| Object is instance of Object | Map is instance of Object |
| Some keys are reserved like constructor,<br>toString, etc. | No restriction over keys. |
| Object static methods like `Object.keys()`<br>or `Object.entries()` or `Object.values()` <br>are required. | Maps are iterable and preserve<br>order of key-value pairs |
| To get size: `Object.keys(exams).length;` | To get size: `exams.size;` |
| For iteration: <br/>```for (const [color, hex] of Object.entries(colorsHex)) {console.log(color, hex);}``` | For iteration: <br/>```for (const [color, hex] of colorsHexMap) {console.log(color, hex);}``` |
|For initializatoin: <br/>```const userCustomFields = {'color': 'blue', 'size': 'medium', 'toString': 'A blue box'}; ```| For initialization: <br/>```const userCustomFieldsMap = new Map([['color', 'blue'], ['size', 'medium'], ['toString', 'A blue box']]);``` |
