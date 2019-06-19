# Its_all_Javascript
A collection of all pure JS (ES6) code snippets 

* ### Sort an array in JS
```javascript
var points = [40, 100, 1, 5, 25, 10];

//ascending
points.sort((a, b) =>  a - b );
console.log('points:', points);
points.sort((a, b) =>  a > b );
console.log('points:', points);

//descending
points.sort((a, b) =>  b - a );
console.log('points:', points);
points.sort((a, b) =>  a < b );
console.log('points:', points);
```
---

* ### indexOf () operator
```javascript
x=[1,2,3]
console.log(x);                         //[ 1, 2, 3 ]
console.log(x[-1]);                     //undefined
x[-1]=5;
console.log(x);                         //[ 1, 2, 3, '-1': 5 ]
console.log(x[-1]);                     //5

console.log(x.indexOf(5));              //-1
console.log(x.indexOf(1000000));        //-1
console.log(x.indexOf(254982));         //-1
// indexOf() looks for a value in an array, if it does not find it,
// it returns -1

console.log(x[x.indexOf(5)]);           //5
console.log(x[x.indexOf(1000000)]);     //5
console.log(x[x.indexOf(254982)]);      //5
```
---

* ### Capitalize first letter of each word
    Using the JavaScript language, have the function LetterCapitalize(str) take the str parameter being passed and capitalize the first letter of each word. Words will be separated by only one space.
```javascript
function LetterCapitalize(str) {
    let foo = str.split(" ");
    for(let i=0 ; i<foo.length ; i++){
       foo[i] = foo[i].charAt(0).toUpperCase() + foo[i].substring(1);
    }
    foo = foo.join(" ");
    return foo;
}
     
console.log('answer:', LetterCapitalize("i ran there"));
```
---

* ### Change letter
    Using the JavaScript language, have the function LetterChanges(str) take the str parameter being passed and modify it using the following algorithm.   Replace every letter in the string with the letter following it in the alphabet (ie. c becomes d, z becomes a). Then capitalize every vowel in this new string (a, e, i, o, u) and finally return this modified string.  
       
    Input : "hello*3"  Output : "Ifmmp*3" Input : "fun times!" Output : "gvO Ujnft!" 
```javascript
function LetterChanges(str) { 
    let copy = str;
    for (let i = 0; i < str.length; i++) {
        if(copy[i].match(/^[A-Za-z]+$/)){
            let foo = String.fromCharCode(copy.charCodeAt(i) + 1);
            // console.log('foo', foo);
            // console.log('copy', copy);
            copy = copy.replace( copy[i] , foo);
        }
    }
    for (let i = 0; i < copy.length; i++) {
        if(copy[i].match(/[aeiouAEIOU]/)){
            copy = copy.replace(copy[i],copy[i].toUpperCase());
            // console.log('copy:', copy);
        }
    }
    return copy;       
}
 
console.log('answer:', LetterChanges("hello*3")); 
console.log('answer:', LetterChanges("fun times!"));
```
---
* ### Find sum of all border elements of a matrix
```javascript
const a = [
    [1,1,1,1,1],
    [5,1,1,1,7],
    [3,1,1,1,5],
    [2,2,2,2,2]
]

const nrows = a.length;         //4
const ncols = a[0].length;      //5

const arrSum = arr => arr.reduce((total,no) => total + no, 0)
// console.log(arrSum([1,2,3]));

console.log('sum of first row', arrSum(a[0]));               //sum of first row
console.log('sum of last row', arrSum(a[nrows - 1]));        //sum of last row
sum = arrSum(a[0]) + arrSum(a[nrows - 1]) ;

for (let i = 1; i < nrows-1 ; i++) {
    sum += a[i][0] + a[i][ncols - 1];
}                                                // adding first n last ele of remaining rows

console.log('sum of border elements of matrix is:', sum)
```
---

* ### Max () operator
```javascript
console.log(Math.max());
// -Infinity

console.log( Math.max([1,2,3]));
// NaN

console.log( Math.max(...[1,2,3]));
// 3
```
---

* ### Number.MIN_VALUE 
    Number.MIN_VALUE is a number closest to zero that can be represented in js
```javascript
let i = Number.MIN_VALUE;
console.log('i:', i);           //5e-324

console.log(i*i);               //0
console.log(i+1);               //1
console.log(i-1);               //-1
console.log(i/i);               //1
```
---

* ### Title
```javascript
code
```
---

* ### Fetch and query data from an API using Axios in node
```javascript
const axios = require('axios');

async function getData(){
    try {
        const blob = await axios.get('http://www.espncricinfo.com/ci/engine/match/1157752.json'); 
        console.log("data successfully fetched");
        // console.log('innings', blob.data.innings[0].runs);
        const i1 = blob.data.innings[0].runs;
        const w1 = blob.data.innings[1].runs;
        const w2 = blob.data.innings[2].runs;
        console.log("Runs scored by India in first inning : "+ i1);
        console.log("Runs scored by West Indies in first inning : "+ w1);
        console.log("India enforced a follow-on");
        console.log("Runs scored by West Indies in second inning : "+ w2);
    } catch (error) {
        console.log("error fetching");
    }   
}
getData();
```
---
* ### Check wether input scentence is palindrome or not
```javascript
const readline = require('readline').createInterface({input: process.stdin,output: process.stdout})

readline.question(`Enter a scentence to check if its a palindrome or not:`, (scentence) => {
    s1 = scentence.replace(/\s/g,'').trim().toLowerCase();
    const rev = s1.split("").reverse().join("");
    if(s1==rev){result='a'}
    else{result='not a'}
    console.log(`The scentence "${scentence}" is ${result} palindrome`);
    readline.close()
})
```
---

* ### creating a reusable method using Array.prototype

```javascript
const Students = [];
class Student{
    constructor(name,course,college){
        this.name=name;
        this.course=course;
        this.college=college;
        Students.push(this);
    }
}
const s1=new Student('Priya','BE','Thakur');
const s2=new Student('Rohan','MS','Stevens');
const s3=new Student('Jay','BE','Thadomal');
const s4=new Student('Mansi','ME','Thakur');
const s5=new Student('Sneha','Diploma','Thakur');

// Grouping students by specified college name
const thakurStudents = Students.filter((student) => {
    if(student.college == 'Thakur'){
        return true;
    }
});
console.log("Students from college Thakur :");
console.table(thakurStudents);

// Generalising - creating a reusable method that can be used to group by any property name
Array.prototype.groupBy = function(prop) {
    return this.reduce(function(groups, item) {
      const val = item[prop]
      groups[val] = groups[val] || []
      groups[val].push(item)
      return groups
    }, {})
};

const collegeGroup = Students.groupBy('college');
console.log("Grouping by college name:")
console.log(collegeGroup);
```
---

* ### Input output from terminal in node
```javascript
const readline = require('readline').createInterface({input: process.stdin,output: process.stdout})

readline.question(`Enter your name: `, (name) => {
    console.log(`Hello ${name}, Welcome`);
    readline.close()
})
```
---
* ### Javascript Clock
```javascript
const secondHand = document.querySelector('.sec');
const minuteHand = document.querySelector('.min');
const hourHand = document.querySelector('.hour');

function setDate() {
   const now = new Date();
   //console.log(now);
   const seconds = now.getSeconds();
   const minutes = now.getMinutes();
   let hours = now.getHours();
   if (hours > 12) {
       hours = hours - 12;
   }
   console.log(` ${hours}hr ${minutes}min ${seconds}sec`);
   // 0s is 0deg , 30s is 180deg , 60s is 360deg
   // 1hr 30deg ,3hr 90deg , 6hr 180deg, 12hr 0deg 
   const secondDegrees = ((seconds/60) * 360) - 90 ;
   const minuteDegrees = ((minutes/60) * 360) - 90 ;
   const hourDegrees = ((hours/12) * 360) - 90 ;
   //console.log(secondDegrees);
   secondHand.style.transform = `rotate(${secondDegrees}deg)` ;
   minuteHand.style.transform = `rotate(${minuteDegrees}deg)` ;
   hourHand.style.transform = `rotate(${hourDegrees}deg)` ;

}
setInterval(setDate,1000);
```
---
* ### Ajax request to an API
```javascript
var ourRequest = new XMLHttpRequest();
ourRequest.open('GET','https://poojavpatel.github.io/ajaxtest/pets.json');
ourRequest.onload = function(){
	console.log(ourRequest.responseText);

	ourData = ourRequest.responseText;
	console.log(ourData[0]);  /* returns only [ */
	a = ourData[1].species;
	console.log(a);  /*this is undefined:( */
	/*happens as browser sees it as text file | we need to specify its JSON*/

	myData = JSON.parse(ourRequest.responseText);
	console.log(myData[0]);
	a = myData[1].species;
        b = myData[1].name;
        c = myData[1].foods.likes[1];
	console.log(a,b,c);

};
ourRequest.send();
```
---
* ### Title
```javascript
code
```
---




* ### Title
```javascript
code
```
---