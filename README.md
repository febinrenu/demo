# EXP 1 - Student Dashboard

## Program

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,

      home: Scaffold(
        appBar: AppBar(
          title: const Text('Student Dashboard'),
          backgroundColor: Colors.blue,
        ),

        body: Column(
          children: [

            // Container
            Container(
              width: double.infinity,
              color: Colors.amber,
              padding: const EdgeInsets.all(20),
              child: const Text(
                'Welcome, Johann!',
                textAlign: TextAlign.center,
              ),
            ),

            // Row
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceEvenly,
              children: const [
                Icon(Icons.home, size: 30),
                Icon(Icons.book, size: 30),
                Icon(Icons.person, size: 30),
              ],
            ),

            // Expanded and ListView
            Expanded(
              child: ListView(
                children: const [

                  Card(
                    child: ListTile(
                      leading: Icon(Icons.school),
                      title: Text('Computer Science'),
                      subtitle: Text('Department'),
                    ),
                  ),

                  Card(
                    child: ListTile(
                      leading: Icon(Icons.code),
                      title: Text('Flutter'),
                      subtitle: Text('Mobile App Development'),
                    ),
                  ),

                  Card(
                    child: ListTile(
                      leading: Icon(Icons.cloud),
                      title: Text('Cloud Computing'),
                      subtitle: Text('Course'),
                    ),
                  ),

                  Card(
                    child: ListTile(
                      leading: Icon(Icons.storage),
                      title: Text('Database Management'),
                      subtitle: Text('Course'),
                    ),
                  ),

                ],
              ),
            ),
          ],
        ),

        // Bottom Navigation Bar
        bottomNavigationBar: BottomNavigationBar(
          items: const [
            BottomNavigationBarItem(
              icon: Icon(Icons.home),
              label: 'Home',
            ),
            BottomNavigationBarItem(
              icon: Icon(Icons.book),
              label: 'Courses',
            ),
            BottomNavigationBarItem(
              icon: Icon(Icons.person),
              label: 'Profile',
            ),
          ],
        ),
      ),
    );
  }
}





# EXP 2 - Responsive UI Using Flutter

## Program

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,

      home: Scaffold(
        appBar: AppBar(
          title: const Text('Responsive UI'),
          backgroundColor: Colors.blue,
        ),

        body: LayoutBuilder(
          builder: (context, constraints) {

            if (constraints.maxWidth < 600) {

              // Mobile Layout
              return Column(
                children: [
                  Card(
                    child: ListTile(
                      title: Text('Student'),
                    ),
                  ),

                  Card(
                    child: ListTile(
                      title: Text('Courses'),
                    ),
                  ),
                ],
              );

            } else {

              // Desktop / Tablet Layout
              return Row(
                children: [
                  Expanded(
                    child: Card(
                      child: ListTile(
                        title: Text('Student'),
                      ),
                    ),
                  ),

                  Expanded(
                    child: Card(
                      child: ListTile(
                        title: Text('Courses'),
                      ),
                    ),
                  ),
                ],
              );

            }
          },
        ),
      ),
    );
  }
}




# EXP 3 - Student Form Using Flutter

## Program

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final formKey = GlobalKey<FormState>();

    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: const Text('Student Form'),
        ),

        body: Padding(
          padding: const EdgeInsets.all(20),

          child: Form(
            key: formKey,

            child: Column(
              children: [
                TextFormField(
                  decoration: const InputDecoration(
                    labelText: 'Name',
                  ),
                  validator: (value) {
                    if (value == null || value.isEmpty) {
                      return 'Enter name';
                    }
                    return null;
                  },
                ),

                TextFormField(
                  decoration: const InputDecoration(
                    labelText: 'Email',
                  ),
                ),

                TextFormField(
                  obscureText: true,
                  decoration: const InputDecoration(
                    labelText: 'Password',
                  ),
                ),

                ElevatedButton(
                  onPressed: () {
                    if (formKey.currentState!.validate()) {
                      print('Success');
                    }
                  },
                  child: const Text('Submit'),
                ),
              ],
            ),
          ),
        ),
      ),
    );
  }
}




# EXP 4 - Image Gallery Using Flutter

## Program

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        appBar: AppBar(
          title: const Text('Image Gallery'),
        ),
        body: Center(
          child: Image.asset(
            'assets/images/flutter.png',
            width: 200,
            height: 200,
          ),
        ),
      ),
    );
  }
}



# EXP 6 - Animation Using Flutter

## Program

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MaterialApp(home: MyApp()));
}

class MyApp extends StatefulWidget {
  @override
  State<MyApp> createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  bool change = false;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Animation')),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            AnimatedContainer(
              duration: Duration(seconds: 1),
              width: change ? 200 : 100,
              height: change ? 200 : 100,
              color: Colors.blue,
            ),
            ElevatedButton(
              onPressed: () {
                setState(() {
                  change = !change;
                });
              },
              child: Text('Animate'),
            ),
          ],
        ),
      ),
    );
  }
}





# EXP 5 - Navigation Between Multiple Screens Using Flutter

## main.dart

```dart
import 'package:flutter/material.dart';
import 'home.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: const HomePage(),
    );
  }
}
```

## home.dart

```dart
import 'package:flutter/material.dart';
import 'profile.dart';

class HomePage extends StatelessWidget {
  const HomePage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Home')),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.push(
              context,
              MaterialPageRoute(
                builder: (context) => const ProfilePage(),
              ),
            );
          },
          child: const Text('Go to Profile'),
        ),
      ),
    );
  }
}
```

## profile.dart

```dart
import 'package:flutter/material.dart';
import 'details.dart';

class ProfilePage extends StatelessWidget {
  const ProfilePage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Profile')),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.push(
              context,
              MaterialPageRoute(
                builder: (context) => const DetailsPage(),
              ),
            );
          },
          child: const Text('View Details'),
        ),
      ),
    );
  }
}
```

## details.dart

```dart
import 'package:flutter/material.dart';

class DetailsPage extends StatelessWidget {
  const DetailsPage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Details')),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.pop(context);
          },
          child: const Text('Go Back'),
        ),
      ),
    );
  }
}
```




# EXP 7 - Student List Using Flutter

## Program

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {

    List<String> students = [];

    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: const Text('Student List'),
        ),

        body: StatefulBuilder(
          builder: (context, setState) {
            return Column(
              children: [
                ElevatedButton(
                  onPressed: () {
                    Map<String, dynamic> data = {
                      'name': 'Raj'
                    };

                    setState(() {
                      students.add(data['name']);
                    });
                  },
                  child: const Text('Add Student'),
                ),

                Column(
                  children: students
                      .map((name) => Text(name))
                      .toList(),
                ),
              ],
            );
          },
        ),
      ),
    );
  }
}
```
