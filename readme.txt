

+--------+---------+-------------------+------+----------+
| UID_PK | Name    | Email             | Age  | Location |
+--------+---------+-------------------+------+----------+
|      1 | "David" | "david@email.com" |   99 | "SF"     |
|      9 | "Alice" | "alice@email.com" |   28 | "Berlin" |
+--------+---------+-------------------+------+----------+

{
  “users”:{
            "1" : {
              "Name": "David",
              "Email": "david@email.com",
              "Age": "99",
              "Location": "SF”,
              “age_location”: “99_SF”
          },
          “9”: {
              "Name": "Alice",
              "Email": "alice@email.com",
              "Age": "28",
              "Location": "Berlin”,
              “age_location”: “28_Berlin”
          },
        }
}


// Root reference for Firebase
	
const rootRef = firebase.database().ref();



Select By UID

SQL
SELECT * FROM Users WHERE UID = 1;

Firebase
const oneRef = rootRef.child(‘users’).child(‘1’);


Select By Email

SQL
SELECT * FROM Users WHERE Email = “info@dineth.me;

Firebase
const twoRef = rootRef.child(‘users’).orderByChild(‘email’).equalTo(‘info@dineth.me’);


Limit Users to 10

SQL
SELECT * FROM Users LIMIT 10;

Firebase
const threeRef = rootRef.child(‘users’).orderByKey().limitToFirst(10);
const threeRef = rootRef.child(‘users’).limitToFirst(10);


Select all users start name with ‘D’

SQL
SELECT * FROM Users WHERE Name LIKE ‘D%’;

Firebase
const fourRef = rootRef.child(‘users’).orderByChild(‘name’).startAt(‘D’).endAt(‘D\uf*ff’) ;


Select all users age less than 50

SQL
SELECT * FROM Users WHERE Age < 50;

Firebase
const fiveRef = rootRef.child(‘users’).orderByChild(‘age’).endAt(49) ;


Select all users age greater than 50

SQL
SELECT * FROM Users WHERE Age > 50;

Firebase
const sixRef = rootRef.child(‘users’).orderByChild(‘age’).startAt(51) ;


Select all users age between 20 and 100

SQL
SELECT * FROM Users WHERE Age > = 20 && Age <= 100;

Firebase
const sevenRef = rootRef.child(‘users’).orderByChild(‘age’).startAt(20).endAt(100) ;


Select all users who are age 28 and live in Berlin

SQL
SELECT * FROM Users WHERE Age  = 28 && Location = ‘Berlin’

Firebase
const sevenRef = rootRef.child(‘users’).orderByChild(‘age_location’).equalTo(’28_Berlin’);
