# Object vs Map


| Object | Map |
|--------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Keys can be simple data types <br>i.e. integer or string or<br>symbol which are further<br>converted to string. | Keys can be of any type.<br>Arrays and Objects are also<br>accepted as keys. Key types<br>are preserved. |
| original order of elements (pairs)<br>is not preserved. | Order of elements (pairs)<br>is preserved. |
| Object is instance of Object | Map is instance of Object |
| Some keys are reserved like constructor,<br>toString, etc. | No restriction over keys. |
| Object static methods like Object.keys()<br>or Object.entries() or Object.values() <br>are required. | Maps are iterable and preserve<br>order of key-value pairs |
| Object.keys(exams).length; | exams.size; |
| for (const [color, hex] of Object.entries(colorsHex)) {<br>  console.log(color, hex);<br>} | for (const [color, hex] of colorsHexMap) {<br>  console.log(color, hex);<br>} |
| const userCustomFields = {<br>  'color':    'blue',<br>  'size':     'medium',<br>  'toString': 'A blue box'<br>}; | const userCustomFieldsMap = new Map([<br>  ['color', 'blue'],<br>  ['size', 'medium'],<br>  ['toString', 'A blue box']<br>]); |
