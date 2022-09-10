# Firestore-For-Beginners-In-Java-Hebrew-


### יצרת מופע של מאגר הנתונים
 ```java
FirebaseFirestore database = FirebaseFirestore.getInstance();
 ```
# Collection גישה ל
```java
 firebase.collection("שם הקולקצייה");
```
# Collectionהוספת אובייקט ל
### User לדוגמא נכניס אובייקט מסוג המחלקה 
### User:

```java
private String username;
private String password;
private int id;

//constructors בנאים
....
//getters & setters
....
```
### הכנסת האובייקט
```java
User user1 = new User("myUsername","myPassword",1); //User יצירת אובייקט מסוג
database.collection("Users").add(user1);//"Users" בשם collectionהכנסתו ל
```

### firebaseתצוגת הנתונים ב
![image](https://user-images.githubusercontent.com/62130401/189478026-3241c076-5592-48a2-869f-c468c69ab304.png)


# שאילתות
## קבלת אובייקט מסויים על ידי פרמטר מזהה
### לדוגמה: קבלת משתמש עם מזהה 1

```java
         database.collection("Users").whereEqualTo("id",1).get().addOnSuccessListener(new OnSuccessListener<QuerySnapshot>() {
             @Override
             public void onSuccess(QuerySnapshot queryDocumentSnapshots) {
                 for (DocumentSnapshot document : queryDocumentSnapshots.getDocuments() ){
                 
                     User userWithId_1 = document.toObject(User.class); //המרת האובייקט 
                     Log.d("user", userWithId_1.getUsername());//מדפיס את שם המשתמש של האובייקט שהוחזר
                 }
             }
         });
```
