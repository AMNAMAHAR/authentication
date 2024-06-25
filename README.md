
🔐 Firebase Authentication with Firestore in Flutter
This project demonstrates how to implement Firebase Authentication and Firestore in a Flutter application. It includes basic authentication functionalities like getting user details and signing out.

🚀 Features
📦 Firebase Authentication: Securely authenticate users using Firebase Auth.
🔍 Get User Details: Retrieve authenticated user details from Firestore.
⏏️ Sign Out: Allow users to securely sign out.
🛠️ Setup Instructions
Add Firebase to your Flutter app:

Follow the official Firebase documentation: Add Firebase to your Flutter app.
Add Dependencies:
Add the following dependencies in your pubspec.yaml file:

yaml
Copy code
dependencies:
  flutter:
    sdk: flutter
  firebase_core: latest_version
  firebase_auth: latest_version
  cloud_firestore: latest_version
Initialize Firebase:
Initialize Firebase in your main.dart file:

dart
Copy code
import 'package:flutter/material.dart';
import 'package:firebase_core/firebase_core.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Firebase.initializeApp();
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Firebase Auth',
      home: Scaffold(
        appBar: AppBar(
          title: Text('Flutter Firebase Auth'),
        ),
        body: Center(child: Text('Welcome to Flutter Firebase Auth!')),
      ),
    );
  }
}
📚 Usage
Get User Details
To fetch the current user's details from Firestore:

dart
Copy code
AuthMethods authMethods = AuthMethods();
authMethods.getUserDetails().then((user) {
  print("User: ${user.username}");
}).catchError((error) {
  print("Error: $error");
});
Sign Out
To sign out the current user:

dart
Copy code
authMethods.signOut().then((_) {
  print("User signed out successfully.");
}).catchError((error) {
  print("Error signing out: $error");
});
🔧 Firestore Setup
Firestore Rules:
Ensure your Firestore rules allow authenticated users to read and write their own data:

plaintext
Copy code
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
User Data Structure:
Ensure your Firestore users collection has documents with fields uid, email, and username.

📝 License
This project is licensed under the MIT License - see the LICENSE file for details.




![Screenshot_20240625-103719](https://github.com/AMNAMAHAR/authentication/assets/158574242/ba6c131f-44c9-4098-9d6f-109b6a9ba0d8) 


![Screenshot_20240625-103726](https://github.com/AMNAMAHAR/authentication/assets/158574242/eb37ad6b-78fe-4623-a4af-d5afdb9596c1)

